<template>
    <div class="pagination-container">
      <!-- Tombol Previous -->
      <button
        :disabled="currentPage === 1"
        @click="goToPage(currentPage - 1)"
        class="pagination-button"
      >
        Previous
      </button>
  
      <!-- Tampilkan halaman pertama (1) dan kedua (2) -->
      <button
        v-for="page in [1, 2]"
        :key="page"
        @click="goToPage(page)"
        :class="['pagination-button', { active: currentPage === page }]"
      >
        {{ page }}
      </button>
  
      <!-- Tampilkan titik-titik jika halaman saat ini bukan halaman 3 -->
      <span v-if="currentPage > 3">...</span>
  
      <!-- Tampilkan halaman saat ini jika bukan halaman awal atau akhir -->
      <button
        v-if="currentPage > 2 && currentPage < totalPages - 1"
        @click="goToPage(currentPage)"
        :class="['pagination-button', 'active']"
      >
        {{ currentPage }}
      </button>
  
      <!-- Tampilkan titik-titik jika halaman saat ini tidak dekat dengan halaman terakhir -->
      <span v-if="currentPage < totalPages - 2">...</span>
  
      <!-- Tampilkan dua halaman terakhir -->
      <button
        v-for="page in totalPages > 3 ? [totalPages - 1, totalPages] : [totalPages]"
        :key="page"
        @click="goToPage(page)"
        :class="['pagination-button', { active: currentPage === page }]"
        >
        {{ page }}
      </button>

      <!-- Tampilkan satu halaman terakhir -->
      <!-- <button
        @click="goToPage(totalPages)"
        :class="['pagination-button', { active: currentPage === totalPages }]"
      >
        {{ totalPages }}
      </button> -->
  
      <!-- Tombol Next -->
      <button
        :disabled="currentPage === totalPages"
        @click="goToPage(currentPage + 1)"
        class="pagination-button"
      >
        Next
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['currentPage', 'totalPages'],
    methods: {
      goToPage(page) {
        if (page >= 1 && page <= this.totalPages) {
          this.$emit('change-page', page);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .pagination-container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 5px;
  }
  
  .pagination-button {
    padding: 5px 10px;
    border: 1px solid #ccc;
    background-color: white;
    cursor: pointer;
    border-radius: 5px;
  }
  
  .pagination-button.active {
    background-color: rgb(172, 214, 178);
    color: white;
  }
  
  .pagination-button:disabled {
    background-color: #e9ecef;
    cursor: not-allowed;
  }
  </style>
  