<template>
  <div class="flex flex-col justify-center min-h-screen bg-gray-100 items-center p-8">
    <h1 class="text-xl font-bold mb-6">Контакты</h1>

    <transition name="fade">
      <div
        v-show="isFormSended"
        class="absolute bg-green-400 shadow-md p-4 text-white flex justify-between"
      >
        <div class="mr-4">Сообщение отправлено</div>
        <button @click="isFormSended = false">&#10006;</button>
      </div>
    </transition>
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
      <textarea
        v-model="message"
        placeholder="Message"
        required
        class="custom-input mb-8"
      />
      <button
        type="submit"
        class="custom-purple-btn"
      >
        Отправить
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
      message: null,
      isFormSended: false
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

      if (!this.message) {
        this.errors.push('Укажите сообщение.');
      } else if (this.message.length > 150) {
        this.errors.push('Максимальная длина сообщения - 150 символов.');
      }

      if (!this.errors.length) {
        // await this.postFromData()
        this.postFromData()
        this.isFormSended = true;
      }

      e.preventDefault();
    },
    validEmail (email) {
      let re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    async postFromData () {
      await this.$axios.$post('/api/v1/contact', {
        name: this.name,
        email: this.email,
        message: this.message
      })
    }
  }
}
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
