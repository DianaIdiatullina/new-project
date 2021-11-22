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
      <h2 class="text-xl font-bold mb-2">
        {{ item.title }} {{ item.city }}
      </h2>
      <div>{{ item.price }}</div>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      vacancies: [
        {
          title: '123',
          city: 'xvffdxb',
          key: '123',
          price: '1778'
        },
        {
          title: '1234',
          city: 'xvffdxb',
          key: '1234',
          price: '1778'
        }
      ],
    }
  },
}
</script>

<style scoped>

</style>
