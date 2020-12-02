<template>
    <nav class="navbar navbar-expand navbar-light fixed-top">
      <div class="container">
        <a href="#" class="navbar-brand">Home</a>
        <div class="collaps navbar-collapse">
          <ul class="navbar-nav ml-auto" v-if="!user">
            <li class="nav-item">
              <router-link to="/login" class="nav-link">Login</router-link>
            </li>
            <li class="nav-item">
              <router-link to="/register" class="nav-link">Sign up</router-link>
            </li>
          </ul>
          <ul class="navbar-nav ml-auto" v-else>
            <li class="nav-item">
              <a href="javascript:void(0)" @click="handleLogout" class="nav-link">Logout</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>

<script>
export default {
    name: 'AuthenNav',
    props: ['user'],
    methods: {
      handleLogout() {
        localStorage.removeItem('token');
        this.$store.dispatch('user', null);
        this.$route.push('/');
      },
    },
}
</script>