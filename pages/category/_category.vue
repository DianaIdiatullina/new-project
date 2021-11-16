<template>
  <div class="container mx-auto h-full p-4">
    <div class="flex flex-wrap">
      <nuxt-link
        v-for="(item, index) in products"
        :key="index"
        to="/category/cat-1/product"
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
          <div>
            {{ item.price }}
          </div>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [
        {
          title: 'jdndndn',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg',
          price: '400$'
        },
        {
          title: 'ududjdxn',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg',
          price: '400$'
        },
        {
          title: 'djdn mfm df',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg',
          price: '400$'
        },
        {
          title: 'ndxnsn',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg',
          price: '400$'
        }
      ]
    }
  },
}
</script>

<style scoped>

</style>
