<template>
    <div class="page">
      <button :disabled="currentPage === 1" @click="$emit('change-page', currentPage - 1)" class="previous">
        Previous
      </button>
  
      <span>Page {{ currentPage }} of {{ totalPages }}</span>
  
      <button :disabled="currentPage === totalPages" @click="$emit('change-page', currentPage + 1)" class="next">
        Next
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['currentPage', 'totalPages'],
  };
  </script>
  
  <style scoped>
  .page{
    background-color: #f0f0f0;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 5px;
  }
  button {
    padding: 5px 10px;
    margin: 0 5px;
  }
  .next{
    background-color: rgb(99, 207, 114);
  }
  .previous{
    background-color: rgb(172, 214, 178);
  }
  </style>
  
