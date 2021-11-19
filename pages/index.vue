<template>
  <div class="container mx-auto p-4 md:p-8">
    <div class="lg:w-4/6">
      <VueSlickCarousel :dots="true" :autoplay="true">
        <div v-for="banner in banners" :key="banner">
          <nuxt-link to="/category/notebooks">
            <img :src="require(`~/assets/img/${banner}`)" class="object-cover h-60 md:h-80 lg:h-96 w-full">
          </nuxt-link>

        </div>
      </VueSlickCarousel>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  components: { VueSlickCarousel },
  data() {
    return {
      banners: ["slider-1.jpg", "slider-2.jpg", "slider-3.jpg"],
    }
  }
}
</script>

<style>

</style>
