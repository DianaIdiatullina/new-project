<template>
  <div class="relative flex flex-col justify-center min-h-screen bg-gray-100 items-center p-8">
    <h1 class="text-xl font-bold mb-6">Регистрация</h1>

    <form
      @submit.prevent="checkForm"
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
        v-model="name"
        type="text"
        placeholder="Name"
        name="name"
        required
        class="custom-input"
      >
      <input
        v-model="email"
        type="text"
        placeholder="Email"
        name="email"
        required
        class="custom-input"
      >
      <input
        v-model="password"
        type="password"
        placeholder="Password"
        name="password"
        required
        class="custom-input mb-8"
      >
      <button class="custom-purple-btn">
        Зарегистрироваться
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
      name: null,
      email: null,
      password: null,
    }
  },
  methods: {
    async checkForm (e) {
      this.errors = [];

      if (!this.name) {
        this.errors.push('Укажите имя.');
      }
      if (!this.email) {
        this.errors.push('Укажите электронную почту.');
      } else if (!this.validEmail(this.email)) {
        this.errors.push('Укажите корректный адрес электронной почты.');
      }
      if (!this.password) {
        this.errors.push('Укажите пароль.');
      } else if (!this.validPassword(this.password)) {
        this.errors.push('Пароль должен содержать буквы (верхнего и нижнего регистра), цифры, спецсимволы. Длина пароля минимум 8 символов.');
      }

      if (!this.errors.length) {
        await this.postFromData()
        this.$router.push('/')
      }

      e.preventDefault();
    },
    validEmail (email) {
      let re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    validPassword (password) {
      let re = /(?=.*[0-9])(?=.*[!@#$%^&*])(?=.*[a-z])(?=.*[A-Z])[0-9a-zA-Z!@#$%^&*]{6,}/g;
      return re.test(password);
    },
    async postFromData () {
      await this.$axios.$post('http://134.209.194.82:3000/api/signup', {
        name: this.name,
        email: this.email,
        password: this.password
      })
    }
  }
}
</script>

<style scoped>

</style>
