<template>
  <header class="border-b-2">
    <div class="container mx-auto flex justify-between items-center p-4 md:p-8">
      <h2 class="text-xl font-semibold">
        <nuxt-link to="/">Test site</nuxt-link>
      </h2>
      <ul class="flex text-gray-500">
        <li class="text-sm">
          <nuxt-link to="/news">Новости</nuxt-link>
        </li>
        <li class="text-sm ml-4">
          <nuxt-link to="/contact">Контакты</nuxt-link>
        </li>
        <li class="text-sm ml-4">
          <nuxt-link to="/login">Войти</nuxt-link>
        </li>
        <li class="text-sm ml-4">
          <nuxt-link to="/signup">Регистрация</nuxt-link>
        </li>
      </ul>
    </div>

  </header>
</template>

<script>
export default {
  name: "HeaderComponent"
}
</script>

<style scoped>

</style>
