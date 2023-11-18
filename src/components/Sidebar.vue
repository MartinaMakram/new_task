<template>
  <div class="sidebar">
    <CategoryComponent></CategoryComponent>
    <BrandComponent></BrandComponent>
  </div>
</template>

<script>
import CategoryComponent from './Category.vue';
import BrandComponent from './Brand.vue';

export default {
  components: {
    CategoryComponent,
    BrandComponent
  }
};
</script>

<style>
.sidebar {
  display: inline;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 25px;
  position: relative;
  top: 28px;
  left: 5px;
}
</style>

