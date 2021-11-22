<template>
  <div class="container mx-auto h-full p-4">
    <h1 class="text-2xl font-bold mb-4">
      {{ item.title }} {{ item.city }}
    </h1>
    <div>{{ item.price }}</div>
    <div>{{ item.description }}</div>
    <h3 class="font-bold mt-8">Контакты</h3>
    <div>{{ item.contact.name }}</div>
    <div>{{ item.contact.phone }}</div>
    <div>{{ item.contact.email }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      item:
        {
          title: '123',
          city: 'xvffdxb',
          key: '123',
          price: '1778',
          description: 'Корпоративное обучение. График работы: сменный по 12 часов. Возможность карьерного роста. Стабильная заработная плата + премии.',
          contact: {
            name: 'drsfd',
            phone: '439593945',
            email: 'drsfdesfs'
          }
        }
    }
  }
}
</script>

<style scoped>

</style>
