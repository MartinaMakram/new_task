<template>
  <div class="pagination">
    <button @click="goToPage('prev')">&lt;</button>
    <div v-for="page in pages" :key="page" class="page" :class="{ active: currentPage === page }" @click="goToPage(page)">
      {{ page }}
    </div>
    <button @click="goToPage('next')">&gt;</button>
  </div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  props: {
    totalItems: {
      type: Number,
      required: true,
    },
    itemsPerPage: {
      type: Number,
      required: true,
    },
    currentPage: {
      type: Number,
      required: true,
    },
    onPageChange: {
      type: Function,
      required: true,
    },
  },
  setup(props) {
    const pages = ref([]);

    watch(
      () => props.totalItems,
      () => {
        calculatePages();
      }
    );

    watch(
      () => props.currentPage,
      () => {
        calculatePages();
      }
    );

    const calculatePages = () => {
      const totalPages = Math.ceil(props.totalItems / props.itemsPerPage);
      pages.value = Array.from({ length: totalPages }, (_, index) => index + 1);
    };

    const goToPage = (page) => {
      let newPage = props.currentPage;

      if (page === 'prev') {
        newPage = Math.max(1, props.currentPage - 1);
      } else if (page === 'next') {
        newPage = Math.min(pages.value.length, props.currentPage + 1);
      } else {
        newPage = page;
      }

      if (newPage !== props.currentPage) {
        props.onPageChange(newPage);
      }
    };

    return {
      pages,
      goToPage,
    };
  },
};
</script>

<style scoped>

.pagination {
display: flex;
justify-content: center;
align-items: center;
margin-top: 20px;
}

.page {
cursor: pointer;
padding: 8px 12px;
margin: 0 5px;
border: 1px solid #ccc;
border-radius: 4px;
}

.page.active {
background-color: #007bff;
color: #fff;
}

button {
cursor: pointer;
padding: 8px 12px;
margin: 0 5px;
border: 1px solid #ccc;
border-radius: 4px;
}
</style>

