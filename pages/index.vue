<template>
  <div class="container flex flex-wrap mx-auto p-4 md:p-8">
    <div class="w-full lg:w-4/6 lg:pr-10">
      <VueSlickCarousel :dots="true" :autoplay="true" class="mb-8">
        <div v-for="banner in banners" :key="banner">
          <nuxt-link to="/category/notebooks">
            <img :src="require(`~/assets/img/${banner}`)" class="object-cover h-60 md:h-80 lg:h-96 w-full">
          </nuxt-link>

        </div>
      </VueSlickCarousel>

      <h2 class="font-bold text-lg mb-8">Популярные товары</h2>

      <div class="flex flex-wrap mb-8">
        <nuxt-link
          v-for="(item, index) in products"
          :key="index"
          :to="`/catalog/furniture/${item.key}`"
          class="p-4 w-full md:w-1/3"
        >
          <div class="shadow-lg p-4">
            <img
              :src="item.preview_img"
              class="h-40 lg:h-52 w-full object-contain mb-2"
              alt=""
            >
            <h2 class="text-xl font-semibold text-indigo-400 mb-2">
              {{ item.title }}
            </h2>
            <div>
              {{ item.price }}$
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>

    <div class="w-full lg:w-2/6">
      <h2 class="font-bold text-lg mb-8">Новости компании</h2>
      <div
        v-for="(item, index) in news"
        :key="index"
        class="shadow-lg max-w-screen-md mb-8 p-4"
      >
        <h2 class="text-indigo-400 font-semibold mb-2">
          {{ item.title }}
        </h2>
        <div>
          {{ item.description }}
        </div>
      </div>
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
      news: [],
      products: [],
    }
  },
  created() {
    this.getNews()
    this.getPopularProducts()
  },
  methods: {
    async getNews() {
      let result = await this.$axios.$get('http://134.209.194.82:3000/api/news')
      this.news = result.data
    },
    async getPopularProducts() {
      let result = await this.$axios.$get(`http://134.209.194.82:3000/api/products/popular`)
      this.products = result.data
    }
  }
}
</script>

<style>

</style>
