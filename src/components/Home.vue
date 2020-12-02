<template>
  <div>
    <h3 v-if="user">Hi, {{ user.user_name }}</h3>
    <h3 v-else>You are not logged in</h3>
  </div>
</template>

<script>
import {mapGetters} from 'vuex';

export default {
  name: "Home",
  computed: {
    ...mapGetters(['user'])
  }
}
</script>