<template>
  <div class="filters-container">
    <button 
    @click="toggleFiltersVisibility" 
    class="toggle-btn">{{ showFilters ? 'Hide' : 'Show' }} Filters</button>


    
    <div v-if="showFilters" class="chosen-filters">
      <!-- Selected Categories -->
      <div v-for="(category, index) in chosenCategories" :key="index" class="filter-item">
        {{ category.name }}
        <span @click="removeCategory(index)" class="close-icon">&times;</span>
      </div>

      <!-- Selected Brands -->
      <div v-for="(brand, index) in chosenBrands" :key="index" class="filter-item">
        {{ brand.name }}
        <span @click="removeBrand(index)" class="close-icon">&times;</span>
      </div>

      <!-- Product Counter -->
      <div class="counter">Total Products: {{ productsCount }}</div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const eventBus = {};

export default {
  data() {
    return {
      showFilters: false,
      chosenCategories: [],
      chosenBrands: [],
      productsCount: 0,
    };
  },
  methods: {
    toggleFiltersVisibility() {
      this.showFilters = !this.showFilters;
    },
    removeCategory(index) {
      this.chosenCategories.splice(index, 1);
      this.updateProductsCount();
    },
    removeBrand(index) {
      this.chosenBrands.splice(index, 1);
      this.updateProductsCount();
    },
    updateChosenCategories(selectedCategories) {
      this.chosenCategories = selectedCategories;
      this.updateProductsCount();
    },
    updateChosenBrands(selectedBrands) {
      this.chosenBrands = selectedBrands;
      this.updateProductsCount();
    },
    updateProductsCount() {
      // Calculate the total number of products based on selected categories and brands
      // You need to implement your own logic here based on your data structure
      this.productsCount = 0;
    },
  },
  setup() {
    const updateChosenCategories = ref(null); // Ensure to initialize it as a ref

    const on = (event, callback) => {
      if (!eventBus[event]) {
        eventBus[event] = [];
      }
      eventBus[event].push(callback);
    };

    const emit = (event, ...args) => {
      if (eventBus[event]) {
        eventBus[event].forEach(callback => callback(...args));
      }
    };

    onMounted(() => {
      on('updateSelectedCategories', updateChosenCategories.value);
    });

    onBeforeUnmount(() => {
      // Clean up the event listeners when the component is destroyed
      // Not necessary for this simple example, but good practice
      eventBus['updateSelectedCategories'] = [];
    });

    return { on, emit, updateChosenCategories }; // Expose the ref to the template
  },
};
</script>

<style>

.filters-container {
  margin-top: 20px;
}
.toggle-btn{
  width: 157px;
  height: 32px;
  flex-shrink: 0;
}

.chosen-filters {
  display: flex;
  flex-wrap: wrap;
}

.filter-item {
  background-color: #ddd;
  padding: 5px;
  margin-right: 5px;
  margin-bottom: 5px;
  display: flex;
  align-items: center;
}

.close-icon {
  cursor: pointer;
  margin-left: 5px;
}

.counter {
  margin-top: 10px;
  font-weight: bold;
}
</style>
