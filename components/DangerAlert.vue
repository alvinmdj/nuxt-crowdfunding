<template>
  <div class="bg-red-100 rounded-3xl border-l-4 border-red-500 text-red-700 p-4" role="alert">
    <p class="font-bold">Oops!</p>
    <p>{{ errorMessage }}</p>
  </div>
</template>

<script>
export default {
  props: {
    errorMessage: {
      type: String,
      required: true,
    },
  },
}
</script>