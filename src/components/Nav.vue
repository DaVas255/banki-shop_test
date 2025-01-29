<script lang="ts"></script>

<template>
  <nav class="nav">
    <ul class="nav__list">
      <li class="nav__item"><a href="#">Каталог</a></li>
      <li class="nav__item"><a href="#">Доставка</a></li>
      <li class="nav__item"><a href="#">Оплата</a></li>
      <li class="nav__item"><a href="#">Контакты</a></li>
      <li class="nav__item"><a href="#">О компании</a></li>
    </ul>
  </nav>
</template>

<style scoped lang="scss">
.nav {
  &__list {
    display: flex;
    flex-wrap: wrap;
    gap: 48px;

    @media screen and (max-width: 650px) {
      align-items: center;
      justify-content: center;
      gap: 10px;
    }
  }

  &__item {
    color: #343030;

    :hover {
      text-decoration: underline;
    }
  }
}
</style>
