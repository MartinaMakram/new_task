<template>
  <div class="component">
    <div class="header">Category</div>
    <input v-model="searchCategory" type="text" class="search-bar" placeholder="Search category...">
    <ul class="category-list">
      <li v-for="category in filteredCategories" :key="category.id" class="category-item">
        <input v-model="category.checked" type="checkbox" :id="'category' + category.id" @change="updateSelectedCategories">
        <label class="item-name" :for="'category' + category.id">{{ category.name }}</label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchCategory: '',
      categories: [
        { id: 1, name: 'Category 1', checked: false },
        { id: 2, name: 'Category 2', checked: false },
        // Add more categories as needed
      ]
    };
  },
  computed: {
    filteredCategories() {
      return this.categories.filter(category =>
        category.name.toLowerCase().includes(this.searchCategory.toLowerCase())
      );
    }
  },
  methods: {
    updateSelectedCategories() {
      const selectedCategories = this.categories.filter(category => category.checked);
      this.$root.$emit('updateSelectedCategories', selectedCategories);
    }
  }
};
</script>

<style>
/* Add your styling for the category component here */
.component {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 16px;
}

.header {
  display: flex;
  width: 262px;
  justify-content: space-between;
  align-items: center;
}

.search-bar {
  display: flex;
  padding: 5px;
  align-items: flex-start;
  gap: 12px;
  border-radius: 50px;
  background: #F3F3F3;
  width:50%
}

.category-list {
  list-style: none;
  padding: 0;
  width: 126px;
}

.category-item {
  flex-shrink: 0;
}

.item-name {
  color: #000;
text-align: center;

/* Display 2 */
font-family: Lato;
font-size: 14px;
font-style: normal;
font-weight: 400;
line-height: normal;
}
</style>

