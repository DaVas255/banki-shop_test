<script lang="ts">
import Nav from './Nav.vue'
import Svg from './Svg.vue'

export default {
  components: {
    Nav,
    Svg,
  },
}
</script>

<template>
  <footer class="footer">
    <div class="container">
      <Nav />
      <div class="footer__phone">
        <Svg type="phone" />
        +7 (812) 555-55-55
      </div>
      <div class="footer__address">
        <Svg type="geo" />
        г. Санкт-Петербург, ул. Ефимова, 3
      </div>
    </div>
  </footer>
</template>

<style scoped lang="scss">
.footer {
  padding: 38px 0 38px 96px;
  background-color: #eceaea;

  &__phone {
    display: flex;
    gap: 9px;
    align-items: center;
    color: #343030;
  }

  &__address {
    display: flex;
    gap: 10px;
    align-items: center;
    color: #343030;
  }
}

.container {
  display: flex;
  justify-content: space-between;
}
</style>
