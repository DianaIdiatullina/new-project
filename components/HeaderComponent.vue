<template>
  <header class="border-b-2">
    <div class="container mx-auto flex justify-between items-center p-4 md:p-8">
      <h2 class="text-xl font-semibold">
        <nuxt-link to="/">Test site</nuxt-link>
      </h2>
      <button
        class="group leading-6 font-medium flex items-center text-gray-400 hover:text-gray-500 transition-colors duration-200 py-2"
        @click="openSearch = true"
      >
        <svg width="24" height="24" fill="none" class="text-gray-400 group-hover:text-gray-500 transition-colors duration-200 mr-4"><path d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"></path></svg>
        <span>
          Поиск
        </span>
      </button>
      <ul class="hidden md:flex text-gray-500">
        <li class="text-sm">
          <nuxt-link to="/category">Товары</nuxt-link>
        </li>
        <li class="text-sm ml-4">
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

    <transition name="fade">
      <div
        v-show="openSearch"
        class="modal-container md:py-16"
        @click.self="openSearch = false"
      >
        <div class="modal shadow-xl p-4">
          <div class="flex mb-6 items-center">
            <input
              v-model="search"
              type="text"
              placeholder="Поиск"
              name="search"
              class="block p-4 focus:outline-none border-b-2 w-full mr-2"
            >
            <button class="custom-purple-btn w-40">Искать</button>
          </div>

          <div class="overflow-auto px-4">
            <nuxt-link
              v-for="n in 8"
              :key="n"
              to="/cat"
              class="flex mb-4 p-4 bg-gray-100 rounded-2xl"
            >
              <img
                src="https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg"
                alt=""
                class="w-20 object-contain mr-4"
              >
              <div>
                <h3 class="text-xl font-bold mb-2">
                  Lorem Ipsum
                </h3>
                <div class="text-lg">400$</div>
              </div>
            </nuxt-link>
          </div>

        </div>
      </div>
    </transition>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      openSearch: false,
      search: null,
    }
  },
}
</script>

<style scoped>

</style>
