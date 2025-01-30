<script lang="ts">
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      currentImageIndex: 0,
    }
  },
  methods: {
    closeModal() {
      this.$emit('close')
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.product.images.length
    },
    prevImage() {
      this.currentImageIndex =
        (this.currentImageIndex - 1 + this.product.images.length) % this.product.images.length
    },
  },
}
</script>

<template>
  <div class="modal-overlay" @click.self="closeModal">
    <div class="modal">
      <button class="modal__close" @click="closeModal">×</button>
      <div class="modal__content">
        <div class="modal__slider">
          <img
            :src="product.images[currentImageIndex]"
            :alt="`Image ${currentImageIndex + 1}`"
            class="modal__slider-image"
          />
          <button class="slider__prev" @click="prevImage">‹</button>
          <button class="slider__next" @click="nextImage">›</button>
        </div>

        <div class="modal__details">
          <h2 class="modal__title">{{ product.title }}</h2>
          <p class="modal__description">{{ product.description }}</p>
          <div class="modal__price">
            <div v-if="product.oldPrice" class="modal__old-price">{{ product.oldPrice }} $</div>
            <div v-if="product.newPrice" class="modal__new-price">{{ product.newPrice }} $</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.modal {
  position: relative;

  padding: 30px;
  max-width: 600px;
  width: 90%;

  background-color: #fff;
  border-radius: 8px;

  &-overlay {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;

    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

    background-color: rgba(0, 0, 0, 0.5);
  }

  &__close {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
  }

  &__content {
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  &__slider {
    position: relative;
    width: 100%;
    height: 300px;
    overflow: hidden;
    border-radius: 8px;
  }

  &__slider-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 8px;
  }

  &__title {
    font-size: 24px;
    margin-bottom: 16px;
  }

  &__description {
    font-size: 16px;
    color: #666;
    margin-bottom: 16px;
  }

  &__price {
    display: flex;
    flex-direction: column;
    row-gap: 8px;
    font-size: 20px;
    font-weight: bold;
    color: #333;
  }

  &__old-price {
    text-decoration: line-through;
    color: #999;
  }

  &__new-price {
    font-size: 20px;
    font-weight: bold;
    color: #333;
  }
}

.slider__prev,
.slider__next {
  position: absolute;
  top: 50%;
  width: 35px;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
  color: #fff;
  border: none;
  padding: 8px;
  cursor: pointer;
  border-radius: 50%;
  font-size: 24px;
  z-index: 10;
}

.slider__prev {
  left: 16px;
}

.slider__next {
  right: 16px;
}
</style>
