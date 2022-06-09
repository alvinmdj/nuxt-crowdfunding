<template>
  <div class="project-page">
    <section class="project-header pt-5 px-auto sm:px-40">
      <div class="container mx-auto relative">
        <Navbar />
      </div>
    </section>
    <section class="container project-container px-0 sm:px-40 mx-auto -mt-56">
      <div class="flex mt-3">
        <div class="w-3/4 mr-6">
          <div class="bg-white p-3 mb-3 border border-gray-400 rounded-20">
            <figure class="item-image">
              <img
                :src="campaignDetail.data.image_url ? default_image : '/project-thumbnail-1.jpg'"
                alt="project preview"
                class="rounded-20 w-full"
              />
            </figure>
          </div>
          <div class="flex -mx-2">
            <div
              v-for="(image, index) in campaignDetail.data.images"
              :key="index"
              class="relative w-1/4 bg-white m-2 p-2 border border-gray-400 rounded-20"
            >
              <figure class="item-thumbnail cursor-pointer">
                <img
                  :src="`${$axios.defaults.baseURL}/${image.image_url}`"
                  alt="project preview"
                  class="rounded-20 w-full"
                  @click="changeImage(`${$axios.defaults.baseURL}/${image.image_url}`)"
                />
              </figure>
            </div>
          </div>
        </div>
        <div class="w-1/4">
          <div
            class="bg-white w-full p-5 border border-gray-400 rounded-20 sticky"
            style="top: 15px"
          >
            <h3>Project Leader:</h3>

            <div class="flex mt-3">
              <div class="w-1/4">
                <img
                  :src="`${$axios.defaults.baseURL}/${campaignDetail.data.user.image_url}`"
                  alt="project leader"
                  class="w-full inline-block rounded-full"
                />
              </div>
              <div class="w-3/4 ml-5 mt-1">
                <div class="font-semibold text-xl text-gray-800">
                  {{ campaignDetail.data.user.name }}
                </div>
                <div class="font-light text-md text-gray-400">
                  {{ campaignDetail.data.backer_count }} backer
                </div>
              </div>
            </div>

            <h4 class="mt-5 font-semibold">What will you get:</h4>
            <ul class="list-check my-3">
              <li v-for="(perk, index) in campaignDetail.data.perks" :key="index">
                {{ perk }}
              </li>
            </ul>
            <DangerAlert v-if="errorMessage !== ''" :error-message="errorMessage" />
            <template v-if="$store.state.auth.loggedIn">
              <input
                v-model.number="transaction.amount"
                type="number"
                class="border border-gray-500 block w-full px-6 py-3 mt-4 rounded-full text-gray-800 transition duration-300 ease-in-out focus:outline-none focus:shadow-outline"
                placeholder="Amount in Rp"
                @keyup.enter="fund"
              />
              <button
                class="text-center mt-3 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-medium px-6 py-3 text-md rounded-full"
                @click="fund"
              >
                Fund Now
              </button>
            </template>
            <template v-else>
              <button
                class="text-center mt-3 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-medium px-6 py-3 text-md rounded-full"
                @click="$router.push({ path: '/login' })"
              >
                Sign in to Fund
              </button>
            </template>
          </div>
        </div>
      </div>
    </section>
    <section class="container px-0 sm:px-40 mx-auto pt-8">
      <div class="flex justify-between items-center">
        <div class="w-full md:w-3/4 mr-6">
          <h2 class="text-4xl text-gray-900 mb-2 font-medium">
            {{ campaignDetail.data.name }}
          </h2>
          <p class="font-light text-xl mb-5">
            {{ campaignDetail.data.short_description }}
          </p>

          <div class="relative progress-bar">
            <div
              class="overflow-hidden mb-4 text-xs flex rounded-full bg-gray-200 h-6"
            >
              <div
                :style="`width: ${(campaignDetail.data.current_amount / campaignDetail.data.goal_amount) * 100}%`"
                class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
              ></div>
            </div>
          </div>
          <div class="flex progress-info mb-6">
            <div class="text-2xl">{{ ((campaignDetail.data.current_amount / campaignDetail.data.goal_amount) * 100).toFixed(2) }}%</div>
            <div class="ml-auto font-semibold text-2xl">Rp {{ new Intl.NumberFormat().format(campaignDetail.data.goal_amount) }}</div>
          </div>

          <p class="font-light text-xl mb-5">
            {{ campaignDetail.data.description }}
          </p>
        </div>
        <div class="w-1/4 hidden md:block"></div>
      </div>
    </section>
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
export default {
  name: "ProjectDetailPage",
  async asyncData({ $axios, params }) {
    const campaignDetail = await $axios.$get(`/api/v1/campaigns/${params.id}`);
    return { campaignDetail };
  },
  data() {
    return {
      default_image: '',
      transaction: {
        campaign_id: Number.parseInt(this.$route.params.id),
        amount: undefined,
      },
      errorMessage: '',
    };
  },
  mounted() {
    this.default_image = `${this.$axios.defaults.baseURL}/${this.campaignDetail.data.image_url}`;
  },
  methods: {
    changeImage(url) {
      this.default_image = url;
    },
    async fund() {
      try {
        if (this.transaction.amount === undefined || this.transaction.amount === 0) {
          this.errorMessage = 'Please fill the amount field';
          return
        }
        const response = await this.$axios.post('/api/v1/transactions', this.transaction);
        window.location = response.data.data.payment_url;
      } catch (error) {
        this.errorMessage = 'Something went wrong';
      }
    }
  },
}
</script>