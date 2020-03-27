<template>
  <div class="home">
    <HeaderStore />
    <CarouselStore />
    <CarouselBanner />
    <InstagramSection />
    <PartnerSection />
    <FooterStore />
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";

import HeaderStore from "@/components/HeaderStore.vue";
import CarouselStore from "@/components/CarouselStore.vue";
import CarouselBanner from "@/components/CarouselBanner.vue";
import InstagramSection from "@/components/InstagramSection.vue";
import PartnerSection from "@/components/PartnerSection.vue";
import FooterStore from "@/components/FooterStore.vue";

export default {
  name: "Home",
  components: {
    HeaderStore,
    CarouselStore,
    CarouselBanner,
    InstagramSection,
    PartnerSection,
    FooterStore
  }
};
</script>
