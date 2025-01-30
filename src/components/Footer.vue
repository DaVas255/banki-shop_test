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
  padding: 38px 0;
  background-color: #eceaea;

  @media screen and (max-width: 1280px) {
    padding: 38px 20px;
  }

  nav {
    margin-left: 96px;
    margin-right: 126px;

    @media screen and (max-width: 1380px) {
      margin: 0;
    }
  }

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
    margin-right: -51px;
    color: #343030;

    @media screen and (max-width: 1380px) {
      margin-right: 0;
    }
  }
}

.container {
  display: flex;
  justify-content: space-between;

  @media screen and (max-width: 1070px) {
    flex-direction: column;
    align-items: center;
    row-gap: 15px;
  }
}
</style>
