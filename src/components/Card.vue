<script lang="ts">
import Button from './Button.vue'

export default {
  components: {
    Button,
  },
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
      required: false,
    },
    sealed: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
}
</script>

<template>
  <div class="card">
    <img :src="img" alt="Photo" />
    <div class="card__info">
      <h3 class="card__title">{{ title }}</h3>
      <div class="card__footer">
        <div class="card__price">
          <div class="card__old-price" v-if="oldPrice != null">{{ oldPrice }} $</div>
          <div class="card__new-price" v-if="newPrice != null">{{ newPrice }} $</div>
        </div>
        <div v-if="sealed != true">
          <Button text="Купить" />
        </div>
        <div v-if="sealed" class="card__sealed">Продана на аукционе</div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  max-width: 280px;
  width: 100%;
  border: 1px solid #e1e1e1;

  &__info {
    padding: 20px 24px 24px 24px;
  }

  &__title {
    margin-bottom: 23px;

    font-size: 18px;
    line-height: 27px;
  }

  &__footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__old-price {
    text-decoration: line-through;
    color: #a0a0a0;
    font-weight: 300;
  }

  &__new-price {
    font-size: 16px;
    font-weight: 700;
    line-height: 24px;
  }

  &__sealed {
    font-weight: 700;
    font-size: 16px;
    line-height: 24px;
  }
}
</style>
