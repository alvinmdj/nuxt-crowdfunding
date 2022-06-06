<template>
  <div class="landing-page">
    <div class="px-0 sm:px-40">
      <section class="landing-hero pt-5">
        <div class="header__bg"></div>
        <div class="container mx-auto relative">
          <Navbar />
          <Hero />
        </div>
      </section>
      <Steps />
      <section class="container mx-auto pt-24">
        <div class="flex justify-between items-center">
          <div class="w-auto">
            <h2 class="text-3xl text-gray-900 mb-8">
              Projects you can fund!
            </h2>
          </div>
          <div class="w-auto mt-5">
            <NuxtLink class="text-gray-900 hover:underline text-md font-medium" to="/projects">
              View All
            </NuxtLink>
          </div>
        </div>
        <div class="grid grid-cols-3 gap-4 mt-3">
          <CampaignItem
            v-for="campaign in campaigns.data"
            :key="campaign.id"
            :campaign="campaign"
          />
        </div>
      </section>
    </div>
    <ClientTestimony />
    <div class="cta-clip -mt-20"></div>
    <CallToAction />
    <Footer />
  </div>
</template>

<script>
import CampaignItem from '~/components/CampaignItem.vue';
import Footer from '~/components/Footer.vue';
import CallToAction from '~/components/CallToAction.vue';
import ClientTestimony from '~/components/ClientTestimony.vue';
import Steps from '~/components/Steps.vue';
import Hero from '~/components/Hero.vue';
import Navbar from '~/components/Navbar.vue';

export default {
  name: "IndexPage",
  components: {
    Navbar,
    Hero,
    Steps,
    CampaignItem,
    ClientTestimony,
    CallToAction,
    Footer,
  },
  async asyncData({ $axios }) {
    const campaigns = await $axios.$get("/api/v1/campaigns?limit=6");
    return { campaigns };
  },
}
</script>
