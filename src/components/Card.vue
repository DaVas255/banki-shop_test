<script lang="ts">
import Button from './Button.vue'
import ProductModal from './ProductModal.vue'

export default {
  components: {
    Button,
    ProductModal,
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
    description: {
      type: String,
      required: false,
      default: '',
    },
    images: {
      type: Array,
      required: false,
      default: () => [],
    },
  },
  data() {
    return {
      isModalOpen: false,
    }
  },
  computed: {
    modalProduct() {
      return {
        title: this.title,
        description: this.description,
        oldPrice: this.oldPrice,
        newPrice: this.newPrice,
        images: this.images.length ? this.images : [this.img],
      }
    },
  },
  methods: {
    openModal() {
      if (!this.sealed) {
        this.isModalOpen = true
      }
    },
    closeModal() {
      this.isModalOpen = false
    },
  },
}
</script>

<template>
  <div class="card" :class="{ 'card--sealed': sealed }">
    <img
      :src="img"
      alt="Photo"
      @click="!sealed && openModal()"
      class="card__image"
      :class="{ 'card__image--disabled': sealed }"
    />
    <div class="card__info">
      <h3
        class="card__title"
        @click="!sealed && openModal()"
        :class="{ 'card__title--disabled': sealed }"
      >
        {{ title }}
      </h3>
      <div class="card__footer">
        <div class="card__price">
          <div class="card__old-price" v-if="oldPrice != null">{{ oldPrice }} $</div>
          <div class="card__new-price" v-if="newPrice != null">{{ newPrice }} $</div>
        </div>
        <div v-if="sealed != true">
          <Button text="Купить" :itemId="title" />
        </div>
      </div>
      <div v-if="sealed" class="card__sealed">Продана на аукционе</div>
    </div>

    <ProductModal v-if="isModalOpen" :product="modalProduct" @close="closeModal" />
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

  &__image {
    width: 100%;
    cursor: pointer;

    &--disabled {
      cursor: not-allowed;
      opacity: 0.5;
    }
  }

  &__title {
    margin-bottom: 23px;
    font-size: 18px;
    line-height: 27px;
    cursor: pointer;

    &--disabled {
      cursor: not-allowed;
      opacity: 0.5;
    }
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
    margin-top: 14px;
    font-weight: 700;
    font-size: 16px;
    line-height: 24px;
  }

  &--sealed {
    opacity: 0.5;
  }
}
</style>
