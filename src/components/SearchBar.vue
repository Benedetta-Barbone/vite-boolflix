<script>
  export default {
    name: 'SearchBar',
    data() {
      return {
        query: ''
      };
    },
    methods: {
      handleSearch() {
        this.$emit('search', this.query);
      }
    }
  }
  </script>
  
  <template>
    <div class="search-bar">
      <input
        v-model="query"
        @keyup.enter="handleSearch"
        type="text"
        placeholder="Cerca un film o una serie tv..."
      />
      <button @click="handleSearch">Cerca</button>
    </div>
  </template>
  

  <style scoped>
  .search-bar {
    display: flex;
    justify-content: center;
    margin: 20px 0;
  }
  .search-bar input {
    width: 300px;
    padding: 10px;
    margin-right: 10px;
    border: none;
  border-radius: 5px;
  }
  .search-bar button {
    padding: 10px;
    background-color: #e50914;
    border: none;
    color: white;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>
  