<template>
  <div class="container mx-auto h-full p-4 md:p-8">
    <div
      v-for="(item, index) in news"
      :key="index"
      class="shadow-xl max-w-screen-md mb-8 p-4"
    >
      <img
        :src="item.image"
        class="w-72 mb-2"
        alt=""
      >
      <h2 class="text-xl font-bold mb-2">
        {{ item.title }}
      </h2>
      <div>
        {{ item.description }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "news",
  data() {
    return {
      news: []
    }
  },
  created() {
    this.getNews()
  },
  methods: {
    async getNews() {
      // this.news = await this.$axios.$get('http://134.209.194.82:3000/api/news')
      let result = await this.$axios.$get('http://localhost:3000/news.json')
      this.news = result.news
    }
  }
}
</script>

<style scoped>

</style>
