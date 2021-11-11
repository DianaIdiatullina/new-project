<template>
  <div class="container mx-auto p-4 md:p-8">main page</div>
</template>

<script>
export default {
}
</script>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  .custom-input {
    @apply block shadow-md p-4 mb-2 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent w-full;
  }
  .custom-purple-btn {
    @apply px-8 py-4 text-white bg-purple-500 hover:bg-purple-700 w-full;
  }
}
</style>
