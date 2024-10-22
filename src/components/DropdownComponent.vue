<template>
    <div class="drpdown">
      <label for="limit">Data Per-halaman:</label>
      <select id="limit" :value="selectedLimit" @change="onLimitChange">
        <option v-for="limit in limits" :key="limit" :value="limit">{{ limit }}</option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    props: ['limits', 'selectedLimit'],
    methods: {
      onLimitChange(event) {
        this.$emit('change-limit', event.target.value);
      }
    }
  };
  </script>
  
  <style scoped>
  .drpdown{
    background-color: #f0f0f0; 
    padding: 10px;
    border-radius: 5px;
  }
  select {
    padding: 5px;
    margin-left: 10px;
    background-color: rgb(172, 214, 178);
  }
  
  </style>
  