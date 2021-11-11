<template>
  <header class="container mx-auto flex justify-between items-center p-4 md:p-8 border-b-2">
    <h2 class="text-xl font-semibold">
      <nuxt-link to="/">Logo</nuxt-link>
    </h2>
    <ul class="flex text-gray-500">
      <li class="text-sm">
        <nuxt-link to="/news">Новости</nuxt-link>
      </li>
      <li class="text-sm ml-4">
        <nuxt-link to="/login">Войти</nuxt-link>
      </li>
      <li class="text-sm ml-4">
        <nuxt-link to="/signup">Регистрация</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent"
}
</script>

<style scoped>

</style>
