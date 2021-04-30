<template>
  <div class="container">
    <p class="title">{{ message }}!</p>
    <hr>
    <router-link to="/price">Price Page</router-link>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.id }}, {{ user.name }}
      </li>
    </ul>
  </div>
</template>

<script>
const axios = require('axios');
const url = 'https://jsonplaceholder.typicode.com/users';

export default {
  data() {
    return {
      message: 'Hello World'
    }
  },
  asyncData({ params }) {
    return axios.get(url)
      .then(res => {
        return { users: res.data };
      })
  }
}
</script>

<style>
.title {
  font-family: 'Permanent Marker', cursive;
}

</style>
