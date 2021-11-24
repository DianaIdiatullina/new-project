<template>
  <div class="container mx-auto h-full p-4">
    <div class="flex flex-wrap">
      <nuxt-link
        v-for="(item, index) in products"
        :key="index"
        :to="`/catalog/${route}/${item.key}`"
        class="p-4 w-full md:w-1/3 lg:w-1/4"
      >
        <div class="shadow-xl p-4">
          <img
            :src="item.preview_img"
            class="h-40 lg:h-60 w-full object-contain mb-2"
            alt=""
          >
          <h2 class="text-xl font-bold mb-2">
            {{ item.title }}
          </h2>
          <div>
            {{ item.price }}$
          </div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
      route: null
    }
  },
  created() {
    this.route = this.$route.params.category

    this.getProducts(this.route)
  },
  methods: {
    async getProducts(route) {
      let result = await this.$axios.$get(`http://134.209.194.82:3000/api/categories/${route}`)
      this.products = result.data
    }
  }
}
</script>

<style scoped>

</style>
