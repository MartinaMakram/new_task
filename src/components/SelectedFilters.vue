<template>
  <div class="selected-filters">
    <div v-for="category in selectedCategories" :key="category.id" class="selected-item">
      {{ category.name }}
    </div>
    <div v-for="brand in selectedBrands" :key="brand.id" class="selected-item">
      {{ brand.name }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    selectedCategories: {
      type: Array,
      default: () => [],
    },
    selectedBrands: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style>
.selected-filters {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.selected-item {
  background-color: #ddd;
  padding: 5px;
  display: flex;
  align-items: center;
}
</style>
