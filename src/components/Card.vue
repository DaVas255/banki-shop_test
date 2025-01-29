<script lang="ts">
export default {
  props: {
    img: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    oldPrice: {
      type: String,
      required: false,
    },
    newPrice: {
      type: String,
      required: true,
    },
  },
}
</script>

<template>
  <div class="card">
    <img :src="img" alt="Photo" />
    <h3 class="card__title">{{ title }}</h3>
    <div class="card__price">
      <span class="card__old-price" v-if="oldPrice != null">{{ oldPrice }} ₽</span>
      <span class="card__new-price">{{ newPrice }} ₽</span>
    </div>
  </div>
</template>

<style scoped lang="scss"></style>
