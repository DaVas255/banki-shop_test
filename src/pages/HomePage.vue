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
  methods: {
    handleSearch(query: string) {
      this.$refs.main.handleSearch(query)
    },
  },
}
</script>

<template>
  <div class="wrapper">
    <Header @search="handleSearch" />
    <Main ref="main" />
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
