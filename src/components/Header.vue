<script>
import SearchBar from './SearchBar.vue';

export default {
  name: 'Header',
  components: {
    SearchBar
  },
  methods: {
    handleSearch(query) {
      this.$emit('search', query);
    }
  }
}
</script>

<template>
    <header class="header">
      <div class="logo">Netflix</div>
      <SearchBar @search="handleSearch" />
    </header>
  </template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #141414;
  padding: 10px 20px;
}
.logo {
  color: #e50914;
  font-size: 24px;
  font-weight: bold;
}
</style>