<template>
  <div class="project-page">
    <section class="project-header pt-5 px-auto sm:px-40">
      <div class="container mx-auto relative">
        <Navbar />
      </div>
    </section>
    <section class="px-0 sm:px-40">
      <h2 class="my-5 text-3xl text-gray-900 text-center mb-8">
        All available projects you can fund!
      </h2>
      <div class="grid grid-cols-3 gap-4 mt-3">
        <CampaignItem
          v-for="campaign in campaigns.data"
          :key="campaign.id"
          :campaign="campaign"
        />
      </div>
    </section>
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
import CampaignItem from '~/components/CampaignItem.vue';

export default {
  name: "ProjectsPage",
  components: { CampaignItem },
  async asyncData({ $axios }) {
    const campaigns = await $axios.$get("/api/v1/campaigns");
    return { campaigns };
  },
}
</script>