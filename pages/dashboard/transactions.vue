<template>
  <div class="project-page">
    <section class="dashboard-header pt-5 px-auto lg:px-40">
      <div class="container mx-auto relative">
        <Navbar />
      </div>
    </section>
    <section class="container px-auto lg:px-40 mx-auto pt-8">
      <div class="flex justify-between items-center mb-6">
        <div class="w-3/4 mr-6">
          <h2 class="text-4xl text-gray-900 mb-2 font-medium">Dashboard</h2>
          <ul class="flex mt-2">
            <li class="mr-6">
              <NuxtLink
                class="text-gray-500 hover:text-gray-800"
                to="/dashboard"
              >
                Your Projects
              </NuxtLink>
            </li>
            <li class="mr-6">
              <NuxtLink
                class="text-gray-800 font-bold"
                to="/dashboard/transactions"
              >
                Your Transactions
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>
      <hr />
      <div v-for="transaction in transactions.data" :key="transaction.id" class="block mb-2">
        <div class="w-full lg:max-w-full lg:flex mb-4">
          <div
            class="h-48 lg:h-auto lg:w-48 flex-none bg-cover rounded-t lg:rounded-t-none lg:rounded-l text-center overflow-hidden"
            :style="`background-color: #bbb; background-position: center; background-image: url(${$axios.defaults.baseURL}/${transaction.campaign.image_url}`"
          ></div>
          <div
            class="w-full border-r border-b border-l border-gray-400 lg:border-l-0 lg:border-t lg:border-gray-400 bg-white rounded-b lg:rounded-b-none lg:rounded-r p-8 flex flex-col justify-between leading-normal"
          >
            <div>
              <div class="text-gray-900 font-bold text-xl mb-1">
                {{ transaction.campaign.name }}
              </div>
              <p class="text-sm text-gray-600 flex items-center mb-2">
                Rp {{ new Intl.NumberFormat().format(transaction.amount) }}
                &middot;
                {{ new Date(transaction.created_at).toISOString().substring(0, 10) }}
                &middot;&nbsp;
                <span class="capitalize"> {{ transaction.status }}</span>
              </p>
            </div>
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
  name: "DashboardTransactionsPage",
  middleware: 'auth',
  async asyncData({ $axios }) {
    const transactions = await $axios.$get(`/api/v1/transactions`);
    return { transactions };
  }
}
</script>
