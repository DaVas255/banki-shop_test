<script lang="ts">
import Nav from '@/components/Nav.vue'
import Search from '@/components/Search.vue'

export default {
  components: {
    Nav,
    Search,
  },
}
</script>

<template>
  <header class="header">
    <div class="container">
      <Nav />
      <Search />
    </div>
  </header>
</template>

<style scoped lang="scss">
.header {
  padding: 24px 0 24px 96px;
  border: 1px solid #e1e1e1;

  @media screen and (max-width: 1350px) {
    padding: 24px 20px;
  }
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;

  @media screen and (max-width: 1350px) {
    flex-direction: column;
    row-gap: 15px;
  }
}
</style>
