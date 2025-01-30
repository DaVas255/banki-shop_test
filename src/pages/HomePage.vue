<script lang="ts">
import { defineComponent } from 'vue'
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import Main from '../components/Main.vue'

export default defineComponent({
  components: {
    Header,
    Footer,
    Main,
  },
  methods: {
    handleSearch(query: string) {
      // 使用类型断言来指定 this.$refs.main 的类型
      ;(this.$refs.main as typeof Main).handleSearch(query)
    },
  },
})
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
