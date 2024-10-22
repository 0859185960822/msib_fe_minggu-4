<template>
  <div>
    <DropdownComponent
      :limits="[10, 50, 100]"
      :selectedLimit="limit"
      @change-limit="updateLimit"
    />
    <TableComponent :users="users" />
    <PaginationComponent
      :currentPage="currentPage"
      :totalPages="totalPages"
      @change-page="handlePageChange"
    />
  </div>
</template>

<script>
import TableComponent from './components/TableComponent.vue';
import PaginationComponent from './components/PaginationComponent.vue';
// import PaginationComponent from './components/PaginationComponent1.vue';
import DropdownComponent from './components/DropdownComponent.vue';
import axios from 'axios';

export default {
  components: {
    TableComponent,
    PaginationComponent,
    DropdownComponent,
  },
  data() {
    return {
      users: [],
      currentPage: 1, // Halaman saat ini
      totalPages: 1,  // Total halaman
      limit: 10,      // Batas item per halaman
    };
  },
  methods: {
    fetchUsers() {
      const url = `https://dummyjson.com/users?limit=${this.limit}&skip=${(this.currentPage - 1) * this.limit}`;
      axios.get(url).then((response) => {
        this.users = response.data.users;
        this.totalPages = Math.ceil(response.data.total / this.limit); // Hitung total halaman
      });
    },
    updateLimit(newLimit) {
      this.limit = newLimit;
      this.currentPage = 1; // Reset ke halaman pertama setelah mengubah limit
      this.fetchUsers();
    },
    handlePageChange(newPage) {
      if (newPage >= 1 && newPage <= this.totalPages) {
        this.currentPage = newPage;
        this.fetchUsers();
      }
    }
  },
  mounted() {
    this.fetchUsers();
  }
};
</script>

<style scoped>
div {
  padding: 20px;
  background-color: #f0f0f0;
}
</style>
