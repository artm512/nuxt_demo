<template>
  <div class="container">
    <p class="title">{{ message }}!</p>
    <div><img src="~/assets/cat.jpg" alt=""></div>
    <div class="vuex_area">
      <p class="title">{{ $store.state.message }}</p>
      <button @click="$store.dispatch('updateMessageAction', 'Dispatch with payload')">update</button>
    </div>
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
  asyncData({ error, params }) {
    return axios.get(url)
      .then(res => {
        return { users: res.data };
      })
      .catch(e => {
        // console.log(e.response.status);
        error({ 
          statusCode: e.response.status,
          message: e.message
        })
      });
  }
}
</script>

<style>
.title {
  font-family: 'Permanent Marker', cursive;
}

</style>
