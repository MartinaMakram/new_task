<template>
  <div>
    <Header />
    <Filters />
    <ShopPage />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Filters from './components/Filters.vue';
import ShopPage from './components/ShopPage.vue';

export default {
  components: {
    Header,
    Filters,
    ShopPage,
  },
};
</script>

<style>
</style>
