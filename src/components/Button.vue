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
  data() {
    return {
      isLoading: false,
      isInCart: false,
    }
  },
  methods: {
    handleClick() {
      if (this.text === 'Купить' && !this.isLoading && !this.isInCart) {
        this.isLoading = true
        setTimeout(() => {
          this.isLoading = false
          this.isInCart = true
        }, 2000)
      }
    },
  },
}
</script>

<template>
  <button
    class="button"
    :disabled="isLoading"
    @click="handleClick"
    :class="{ button__done: isInCart, button__loading: isLoading }"
  >
    <Svg v-if="isLoading" type="loading" />
    <Svg v-else-if="isInCart" type="ok" />
    {{ isLoading ? 'Обрабатывается' : isInCart ? 'В корзине' : text }}
  </button>
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

  &__done {
    padding: 14px 12px;
  }

  &__loading {
    font-size: 12px;
    padding: 14px 6px;
  }

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
