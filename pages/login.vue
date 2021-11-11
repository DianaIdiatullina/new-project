<template>
  <div class="relative flex flex-col justify-center min-h-screen bg-gray-100 items-center p-8">
    <h1 class="text-xl font-bold mb-6">Вход</h1>

    <form
      @submit="checkForm"
      :novalidate="true"
      class="bg-white shadow-lg p-8 w-full md:w-8/12 lg:w-4/12"
    >
      <div v-if="errors.length">
        <b class="text-sm">Пожалуйста исправьте указанные ошибки:</b>
        <ul class="list-disc p-4 text-red-400">
          <li v-for="error in errors" class="text-sm">{{ error }}</li>
        </ul>
      </div>
      <input
        v-model="email"
        type="text"
        placeholder="Email"
        name="email"
        required
        class="block shadow-md p-4 mb-2 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent w-full"
      >
      <input
        v-model="password"
        type="password"
        placeholder="Password"
        name="password"
        required
        class="block shadow-md p-4 mb-8 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent w-full"
      >
      <button
        type="submit"
        class="px-8 py-4 text-white bg-purple-500 hover:bg-purple-700 w-full"
      >
        Войти
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "signup",
  data() {
    return {
      errors: [],
      email: null,
      password: null,
    }
  },
  methods: {
    async checkForm (e) {
      this.errors = [];

      if (!this.email) {
        this.errors.push('Укажите электронную почту.');
      } else if (!this.validEmail(this.email)) {
        this.errors.push('Укажите корректный адрес электронной почты.');
      }

      if (!this.password) {
        this.errors.push('Укажите пароль.');
      }

      if (!this.errors.length) {
        // await this.postFromData()
        this.postFromData()
        this.$router.push('/')
      }

      e.preventDefault();
    },
    validEmail (email) {
      let re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    async postFromData () {
      await this.$axios.$post('/api/v1/login', {
        email: this.email,
        password: this.password
      })
    }
  }
}
</script>

<style scoped>

</style>
