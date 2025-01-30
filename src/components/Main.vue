<script lang="ts">
import Card from './Card.vue'

const initialCards = [
  {
    img: '/1.png',
    title: '«Рождение Венеры» Сандро Боттичелли',
    oldPrice: '2 000 000',
    newPrice: '1 000 000',
    desc: 'Описание 1',
    images: ['/1.png', '/2.png', '/3.png', '/4.png'],
  },
  {
    img: '/2.png',
    title: '«Тайная вечеря»  Леонардо да Винчи',
    newPrice: '3 000 000',
    desc: 'Описание 1',
    images: ['/1.png', '/2.png', '/3.png', '/4.png'],
  },
  {
    img: '/3.png',
    title: '«Сотворение Адама» Микеланджело',
    oldPrice: '6 000 000',
    newPrice: '5 000 000',
    desc: 'Описание 1',
    images: ['/1.png', '/2.png', '/3.png', '/4.png'],
  },
  {
    img: '/4.png',
    title: '«Урок анатомии»  Рембрандт',
    desc: 'Описание 1',
    images: ['/1.png', '/2.png', '/3.png', '/4.png'],
    sealed: true,
  },
]

export default {
  components: {
    Card,
  },
  data() {
    return {
      cards: initialCards,
      searchQuery: '',
    }
  },
  computed: {
    filteredCards() {
      if (!this.searchQuery) {
        return this.cards
      }
      return this.cards.filter(card =>
        card.title.toLowerCase().includes(this.searchQuery.toLowerCase()),
      )
    },
  },
  methods: {
    handleSearch(query: string) {
      this.searchQuery = query
    },
  },
}
</script>

<template>
  <main class="main">
    <div class="container">
      <h1 class="main__title">Картины эпохи Возрождения</h1>
      <div class="main__cards">
        <Card
          v-for="card in filteredCards"
          :key="card.title"
          :img="card.img"
          :title="card.title"
          :oldPrice="card.oldPrice"
          :newPrice="card.newPrice"
          :sealed="card.sealed"
          :description="card.desc"
          :images="card.images"
        />
      </div>
    </div>
  </main>
</template>

<style scoped lang="scss">
.main {
  flex: 1;

  &__title {
    margin-top: 45px;
    margin-bottom: 40px;

    color: #343030;
    font-weight: 700;
    font-size: 24px;
    line-height: 36px;
  }

  &__cards {
    display: flex;
    flex-wrap: wrap;
    gap: 32px;

    @media screen and (max-width: 580px) {
      column-gap: 0;
      justify-content: center;
    }
  }

  .container {
    margin-bottom: 20px;
    @media screen and (max-width: 1260px) {
      padding: 0 10px;
    }
  }
}
</style>
