<template>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Nama</th>
          <th>Usia</th>
          <th>Jenis Kelamin</th>
          <th>Tanggal lahir</th>
          <th>Alamat</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td>{{ user.id }}</td>
          <td>{{ user.firstName }} {{ user.lastName }}</td>
          <td>{{ user.age + ' Tahun' }}</td>
          <td>{{ user.gender }}</td>
          <td>{{ user.birthDate }}</td>
          <td>{{ user.address.address }}, {{ user.address.city }}, {{ user.address.state }} ,{{ user.address.postalCode }}, {{ user.address.country }}</td>
        </tr>
      </tbody>
    </table>
  </template>
  
  <script>
  export default {
    props: ['users'],
  };
  </script>
  
  <style scoped>
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th{
    padding: 10px;
    border: 1px solid #ddd;
    text-align: center;
    background-color: rgb(99, 207, 114);
  }
  td {
    padding: 10px;
    border: 1px solid #ddd;
    text-align: left;
    background-color: rgb(172, 214, 178);
  }
  </style>
  