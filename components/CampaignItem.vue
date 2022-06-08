<template>
  <div class="card-project w-full p-5 border border-gray-500 rounded-20">
    <div class="item">
      <figure class="item-image">
        <img
          v-if="campaign.image_url"
          :src="`${$axios.defaults.baseURL}/${campaign.image_url}`"
          alt=""
          class="rounded-20 w-full h-28 lg:h-60 object-cover"
        />
        <img
          v-else
          src="/project-thumbnail-2.jpg"
          alt="project preview"
          class="rounded-20 w-full h-28 lg:h-60 object-cover"
        />
      </figure>
      <div class="item-meta">
        <h4
          :title="campaign.name"
          class="text-3xl font-medium text-gray-900 mt-5 line-clamp-2"
        >
          {{ campaign.name }}
        </h4>
        <p
          :title="campaign.short_description"
          class="text-md font-light text-gray-900 h-12 line-clamp-3"
        >
          {{ campaign.short_description }}
        </p>
        <div class="relative pt-4 progress-bar">
          <div
            class="overflow-hidden mb-4 text-xs flex bg-gray-200 h-3 rounded-lg"
          >
            <div
              :style="`width: ${(campaign.current_amount / campaign.goal_amount) * 100}%`"
              class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-progress progress-striped"
            ></div>
          </div>
        </div>
        <div class="flex progress-info">
          <div>{{ ((campaign.current_amount / campaign.goal_amount) * 100).toFixed(2) }}%</div>
          <div class="ml-auto font-semibold">Rp {{ new Intl.NumberFormat().format(campaign.goal_amount) }}</div>
        </div>
      </div>
      <NuxtLink
        :to="`/projects/${campaign.id}`"
        class="text-center mt-5 button-cta block w-full bg-orange-button hover:bg-green-button text-white font-semibold px-6 py-2 text-lg rounded-full"
      >
        Fund Now
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    campaign: {
      type: Object,
      required: true,
    },
  },
}
</script>