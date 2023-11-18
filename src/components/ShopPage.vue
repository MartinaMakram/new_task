<template>
  <div class="shop-page">
    <Sidebar :categories="categories" />
    <div class="product-frame">
      <ProductList :products="products" />
      <Pagination 
        :totalItems="totalProducts"
        :itemsPerPage="itemsPerPage"
        :currentPage="currentPage"
        :onPageChange="handlePageChange" />
    </div>
  </div>
</template>

<script>
import Sidebar from './Sidebar.vue';
import ProductList from './ProductList.vue';
import Pagination from './Pagination.vue';

export default {
  components: {
    Sidebar,
    ProductList,
    Pagination,
  },
  data() {
    return {
      products: [],
      categories: [],
      totalProducts: 0,
      itemsPerPage: 10,
      currentPage: 1,
    };
  },
  created() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await fetch('https://joulia.dashboard.hamburgermenu.app/api/v1/products');
        const data = await response.json();
        console.log('Received data:', data);

        if (data && Array.isArray(data.data)) {
          this.products = data.data; // Use the 'data' key if available
        } else {
          console.error('Invalid data format. Expected an array in the "data" key.');
        }
      } catch (error) {
        console.error('Error fetching products:', error);
      }
    },
    handlePageChange(newPage) {
      this.currentPage = newPage;
      // Fetch data for the new page
      this.fetchProducts();
    },
  }
};
</script>

<style scoped>
.product-frame {
  display: inline-flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 30px;
}

.shop-page {
  display: flex;
}
</style>
