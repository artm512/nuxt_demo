<template>
  <div class="container">
    <p class="title">{{ message }}!</p>
    <hr>
    <router-link to="/price">Price Page</router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello World'
    }
  }
}
</script>

<style>
.title {
  font-family: 'Permanent Marker', cursive;
}

</style>
