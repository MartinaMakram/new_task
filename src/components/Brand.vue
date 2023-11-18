<template>
  <div class="component">
    <div class="header">Brand</div>
    <input v-model="searchBrand" type="text" class="search-bar" placeholder="Search brand...">
    <ul class="brand-list">
      <li v-for="brand in filteredBrands" :key="brand.id" class="brand-item">
        <input v-model="brand.checked" type="checkbox" :id="'brand' + brand.id" @change="updateSelectedBrands">
        <label :for="'brand' + brand.id">{{ brand.name }}</label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchBrand: '',
      brands: [
        { id: 1, name: 'Brand 1', checked: false },
        { id: 2, name: 'Brand 2', checked: false },
        // Add more brands as needed
      ]
    };
  },
  computed: {
    filteredBrands() {
      return this.brands.filter(brand =>
        brand.name.toLowerCase().includes(this.searchBrand.toLowerCase())
      );
    }
  },
  methods: {
    updateSelectedBrands() {
      const selectedBrands = this.brands.filter(brand => brand.checked);
      this.$root.$emit('updateSelectedBrands', selectedBrands);
    }
  }
};
</script>

<style>
/* Add your styling for the brand component here */
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



.brand-list {
  list-style: none;
  padding: 0;
}

.brand-item {
  margin-bottom: 5px;
}
</style>
