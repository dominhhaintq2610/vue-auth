<template>
  <div id="app">
      <Nav />
      
      <div class="auth-wrapper">
        <div class="auth-inner">
          <router-view></router-view>
        </div>
      </div>
  </div>
</template>

<script>
import Nav from './components/Nav.vue'
import axios from "axios";

export default {
  name: 'App',
  components: {
    Nav
  },
  async created() {
    const response = await axios.get('user');

    this.$store.dispatch('user', response.data);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
