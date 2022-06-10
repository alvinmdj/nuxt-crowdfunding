<template>
  <div class="project-page">
    <section class="dashboard-header pt-5 px-auto lg:px-40">
      <div class="container mx-auto relative">
        <Navbar />
      </div>
    </section>
    <section class="container px-auto lg:px-40 mx-auto pt-8">
      <div class="flex justify-between items-center">
        <div class="w-full mr-6">
          <h2 class="text-4xl text-gray-900 mb-2 font-medium">Dashboard</h2>
        </div>
      </div>
      <div class="flex justify-between items-center">
        <div class="w-3/4 mr-6">
          <h3 class="text-2xl text-gray-900 mb-4">Edit Campaign "{{ campaign.data.name }}"</h3>
        </div>
        <div class="w-1/4 text-right">
          <button
            class="bg-green-button hover:bg-green-button text-white font-bold px-4 py-1 rounded inline-flex items-center"
            @click="save"
          >
            Update
          </button>
        </div>
      </div>
      <div class="block mb-2">
        <div class="w-full lg:max-w-full lg:flex mb-4">
          <div
            class="w-full border border-gray-400 bg-white rounded p-8 flex flex-col justify-between leading-normal"
          >
            <form class="w-full">
              <div class="flex flex-wrap -mx-3 mb-6">
                <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
                  <label
                    class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                  >
                    Campaign Name
                  </label>
                  <input
                    v-model="campaign.data.name"
                    class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    type="text"
                    placeholder="Example: My Campaign"
                  />
                </div>
                <div class="w-full md:w-1/2 px-3">
                  <label
                    class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                  >
                    Price
                  </label>
                  <input
                    v-model.number="campaign.data.goal_amount"
                    class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    type="number"
                    placeholder="Example: 2000000"
                  />
                </div>
                <div class="w-full px-3">
                  <label
                    class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2 mt-3"
                  >
                    Short Description
                  </label>
                  <input
                    v-model="campaign.data.short_description"
                    class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    type="text"
                    placeholder="Short description of your campaign"
                  />
                </div>
                <div class="w-full px-3">
                  <label
                    class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                  >
                    What will backers get
                  </label>
                  <input
                    v-model="campaign.data.perks"
                    class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    type="text"
                    placeholder="Example: Certificate, T-Shirt, Access to the event"
                  />
                </div>
                <div class="w-full px-3">
                  <label
                    class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
                  >
                    Description
                  </label>
                  <textarea
                    v-model="campaign.data.description"
                    class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                    type="text"
                    placeholder="Long description of your campaign"
                  ></textarea>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </section>
    <div class="cta-clip -mt-20"></div>
    <section class="call-to-action bg-purple-progress pt-64 pb-10"></section>
    <Footer />
  </div>
</template>

<script>
export default {
  name: 'DashboardCreatePage',
  middleware: 'auth',
  async asyncData({ $axios, params }) {
    const campaign = await $axios.$get(`/api/v1/campaigns/${params.id}`);
    return { campaign };
  },
  methods: {
    async save() {
      try {
        // check if all fields are filled
        if (
          this.campaign.name === '' ||
          this.campaign.short_description === '' ||
          this.campaign.description === '' ||
          this.campaign.goal_amount === '' ||
          this.campaign.goal_amount === 0 ||
          this.campaign.perks === ''
        ) {
          this.$toast.error('Please fill in all fields');
          return;
        }

        // update campaign
        await this.$axios.put(`/api/v1/campaigns/${this.$route.params.id}`, {
          name: this.campaign.data.name,
          short_description: this.campaign.data.short_description,
          description: this.campaign.data.description,
          goal_amount: this.campaign.data.goal_amount,
          perks: this.campaign.data.perks,
        });
        this.$toast.success('Campaign created successfully');
      } catch (error) {
        this.$toast.error('Something went wrong');
      }
    },
  },
};
</script>