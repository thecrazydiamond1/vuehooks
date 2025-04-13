<template>
    <div>
      <h1 ref="header">User List</h1>
      <ul>
        <li v-for="user in users" :key="user.id">{{ user.name }}</li>
      </ul>
    </div>
  </template>
  
  
  <script>
  export default {
    name: "UserList",
    data() {
      return {
        users: [],
        interval: null,
      };
    },
    beforeCreate() {
      console.log("1. beforeCreate - No data yet:", this.users);
    },
    created() {
      console.log("2. created - Data available:", this.users);
    },
    beforeMount() {
      console.log("3. beforeMount - DOM is not ready.");
    },
    mounted() {
      console.log("4. mounted - DOM ready. Fetching users...");
      this.fetchUsers();
  
  
      // Start a dummy timer
      this.interval = setInterval(() => {
        console.log("Tick...");
      }, 1000);
    },
    beforeUpdate() {
      console.log("5. beforeUpdate - Before DOM update.");
    },
    updated() {
      console.log("6. updated - After DOM update.");
    },
    beforeUnmount() {
      console.log("7. beforeUnmount - Clearing interval.");
      clearInterval(this.interval);
    },
    unmounted() {
      console.log("8. unmounted - Component is destroyed.");
    },
    methods: {
      fetchUsers() {
        fetch("https://jsonplaceholder.typicode.com/users")
          .then(res => res.json())
          .then(data => {
            this.users = data;
          });
      }
    }
  };
  </script>
  