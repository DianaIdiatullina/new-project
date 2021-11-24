<template>
  <div class="container mx-auto h-full p-4 md:p-8">
    <h1 class="text-2xl font-bold p-4 mb-2">
      {{ product.title }}
    </h1>
    <div class="flex flex-wrap w-full">
      <div class="w-full md:w-1/3 p-4">
        <img
          :src="product.image"
          class="h-40 lg:h-80 w-full object-contain mb-2"
          alt=""
        >
      </div>
      <div class="md:w-2/3 p-4">
        <div class="mb-4">
          {{ product.description }}
        </div>
        <div class="text-lg mb-8">
          {{ product.price }}
        </div>
        <button class="custom-purple-btn w-40">
          В корзину
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product:
        {
          title: 'Ноутбук ASUS VivoBook Pro 15',
          image: 'https://ilike.pet/upload/iblock/786/786fc0798233006257d41dc0132f6387.jpg',
          price: '400$',
          description: '15.6" / 1920x1080 (Full HD) / IPS / Intel Core i5 / 3.1 - 4.4ГГц / RAM 16Гб / без HDD / SSD 512 Гб / GeForce RTX 3050 / 4 Гб / без OС / 1.65кг'
        },
    }
  },
}
</script>

<style scoped>

</style>
