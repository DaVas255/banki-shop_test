<script lang="ts">
import Header from '@/components/Header.vue'
import Footer from '@/components/Footer.vue'
import Main from '@/components/Main.vue'

export default {
  components: {
    Header,
    Footer,
    Main,
  },
}
</script>

<template>
  <div class="wrapper">
    <Header />
    <Main />
    <Footer />
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
