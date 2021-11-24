<template>
  <div class="container mx-auto h-full p-4">
    <h1 class="text-2xl font-bold mb-4">
      Вакансии
    </h1>
    <nuxt-link
      v-for="(item, index) in vacancies"
      :key="index"
      :to="`/vacancies/${item.key}`"
      class="block p-4 w-full shadow-lg mb-4"
    >
      <h2 class="text-lg mb-2">
        {{ item.title }}, г. {{ item.city }}
      </h2>
      <div>от {{ item.price.from }}$ до {{ item.price.to }}$</div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      vacancies: [],
    }
  },
  created() {
    this.getVacancies()
  },
  methods: {
    async getVacancies() {
      let result = await this.$axios.$get('http://134.209.194.82:3000/api/vacancies')
      this.vacancies = result.data
    }
  }
}
</script>

<style scoped>

</style>
