<template>
  <div class="container mx-auto h-full p-4">
    <div class="flex flex-wrap">
      <nuxt-link
        v-for="(item, index) in category"
        :key="index"
        to="/category/cat-1"
        class="p-4 w-full md:w-1/3 lg:w-1/4"
      >
        <div class="shadow-xl p-4">
          <img
            :src="item.image"
            class="h-40 lg:h-60 w-full object-contain mb-2"
            alt=""
          >
          <h2 class="text-xl font-bold mb-2">
            {{ item.title }}
          </h2>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      category: [
        {
          title: 'qteueieo',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg'
        },
        {
          title: 'ududjdxn',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg'
        },
        {
          title: 'dunsl',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg'
        },
        {
          title: 'odkdmdmd',
          image: 'https://bipbap.ru/wp-content/uploads/2019/07/04.-risunki-dlya-srisovki-legkie-dlya-devochek.jpg'
        },
        {
          title: 'sddddklll',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg'
        }
      ]
    }
  },
}
</script>

<style scoped>

</style>
