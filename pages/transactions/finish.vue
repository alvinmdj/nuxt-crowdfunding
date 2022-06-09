<template>
  <div class="container mx-auto h-screen flex justify-center items-center">
    <div class="w-full lg:w-1/3 px-10 lg:px-0">
      <div class="flex justify-center items-center mx-auto mt-6 mb-8">
        <img src="/funded-illustration.svg" alt="" class="w-full" />
      </div>
      <div v-if="$router.currentRoute.query.transaction_status === 'pending'">
        <h2 class="font-medium mb-3 text-3xl text-center">
          Wow! Your transaction is pending.
        </h2>
        <p class="text-center font-light">
          Proceed payment as instructed
          <br />
          to complete your transaction.
        </p>
      </div>
      <div v-else>
        <h2 class="font-medium mb-3 text-3xl text-center">
          Yeay! You are super!
        </h2>
        <p class="text-center font-light">
          Your money has ben transferred
          <br />
          to the project owner.
        </p>
      </div>
      <div class="mb-4 mt-6">
        <div class="mb-3">
          <button
            class="block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-4 text-lg rounded-full"
            @click="$router.push({ path: '/' })"
          >
            Fund Other Project
          </button>
        </div>
        <div class="mb-4">
          <button
            class="block w-full bg-transparent border border-gray-500 text-gray-500 hover:bg-green-button hover:border-green-button hover:text-white font-light px-6 py-4 text-lg rounded-full"
            @click="$router.push({ path: '/dashboard' })"
          >
            My Dashboard
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FundSuccessPage",
  layout: "success",
}
</script>