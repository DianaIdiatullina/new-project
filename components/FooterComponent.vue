<template>
  <footer class="bg-gray-100">

    <div class="container relative mx-auto md:flex justify-center p-4 md:p-8">
      <transition name="fade">
        <div
          v-if="isFormSended"
          class="absolute bg-green-400 shadow-md p-4 text-white flex justify-between"
        >
          <div class="mr-4">Oтправлено</div>
          <button @click="isFormSended = false">&#10006;</button>
        </div>
      </transition>

      <div class="w-full md:max-w-sm md:mr-8 mb-4 md:mb-0">
        Подпишитесь и получайте больше скидок
        на весь ассортимент наших товаров!
      </div>

      <form
        @submit.prevent="checkForm"
        :novalidate="true"
        class="w-full flex flex md:max-w-md"
      >
        <div class="w-full mr-4">
          <input
            v-model="email"
            type="text"
            placeholder="Email"
            name="email"
            required
            class="custom-input rounded"
          >
          <div v-if="error" class="text-xs text-red-400 pr-4">
            {{ error }}
          </div>
        </div>

        <button class="h-14 w-14 bg-purple-500 hover:bg-purple-700 rounded flex justify-center items-center p-3">
          <svg style="width:24px;height:24px" class="text-white" viewBox="0 0 24 24">
            <path fill="currentColor" d="M2,21L23,12L2,3V10L17,12L2,14V21Z" />
          </svg>
        </button>
      </form>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent",
  data() {
    return {
      error: null,
      email: null,
      isFormSended: false
    }
  },
  methods: {
    async checkForm (e) {
      this.error = null;

      if (!this.email) {
        this.error = 'Укажите электронную почту.';
      } else if (!this.validEmail(this.email)) {
        this.error = 'Укажите корректный адрес электронной почты.';
      }

      if (!this.error) {
        // await this.postFromData()
        this.isFormSended = true;
      }

      e.preventDefault();
    },
    validEmail (email) {
      let re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
    // async postFromData () {
    //   await this.$axios.$post('http://134.209.194.82:3000/api/contacts', {
    //     email: this.email,
    //   })
    // }
  }
}
</script>

<style scoped>

</style>
