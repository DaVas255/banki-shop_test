<script lang="ts">
import Svg from './Svg.vue'

export default {
  components: {
    Svg,
  },
  props: {
    text: {
      type: String,
      required: true,
    },
  },
}
</script>

<template>
  <button class="button" v-if="text == 'В корзине'">
    <Svg type="ok" />
    {{ text }}
  </button>
  <button class="button" v-if="text != 'В корзине'">{{ text }}</button>
</template>

<style scoped lang="scss">
.button {
  display: flex;
  align-items: center;
  gap: 8px;

  padding: 14px 36px;
  background-color: #403432;
  border: none;

  color: #f4f6f9;
  font-weight: 700;

  &:hover {
    background-color: #776763;
  }

  &:disabled {
    background-color: #c1b4b1;
  }

  &:active {
    background-color: #403432;
  }
}
</style>
