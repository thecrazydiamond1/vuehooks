<template>
    <div>
      <h2>👤 User List From MountApiCall Component</h2>
      <div v-if="loading">Loading users...</div>
      <ul v-else>
        <li v-for="user in users" :key="user.id">
          {{ user.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        users: [],
        loading: true
      };
    },
    mounted() {
      fetch("https://jsonplaceholder.typicode.com/users")
        .then((res) => res.json())
        .then((data) => {
          this.users = data;
          this.loading = false;
        });
    }
  };
  </script>
  