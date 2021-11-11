<template>
  <div>
    <HeaderComponent />
    <div class="container mx-auto h-full">
      <Nuxt />
    </div>
  </div>
</template>

<script>
import HeaderComponent from "../components/HeaderComponent";

export default {
  components: {
    HeaderComponent
  }
}
</script>
