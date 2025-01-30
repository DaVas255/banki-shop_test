<script lang="ts">
import Button from './Button.vue'

export default {
  components: {
    Button,
  },
  data() {
    return {
      searchQuery: '',
    }
  },
  methods: {
    handleSearch() {
      this.$emit('search', this.searchQuery)
    },
  },
}
</script>

<template>
  <div class="search">
    <input
      type="text"
      placeholder="Поиск по названию картины"
      class="search__input"
      v-model="searchQuery"
    />
    <Button text="Найти" @click="handleSearch" />
  </div>
</template>

<style scoped lang="scss">
.search {
  display: flex;

  &__input {
    width: 294px;
    padding: 13px 16px;
    border: 1px solid #e1e1e1;
    color: #343030;

    @media screen and (max-width: 450px) {
      width: 100%;
    }

    &:focus {
      border: 1px solid #b5b5b5;
      outline: none;
    }

    &::placeholder {
      color: #9f9f9f;
    }
  }
}
</style>
