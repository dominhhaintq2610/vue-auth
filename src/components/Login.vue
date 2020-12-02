<template>
  <form class="form-login" @submit.prevent="handleSubmit">
    <div class="d-flex justify-content-center align-items-center mb-2">
      <label class="mb-0 text-left" style="width: 100px" for="">User Name</label>
      <input type="text" class="form-input" v-model="user_name"/>
    </div>

    <div class="d-flex justify-content-center align-items-center mb-2">
      <label class="mb-0 text-left" style="width: 100px" for="">Password</label>
      <input type="password" class="form-input" v-model="password"/>
    </div>

    <button style="width: fit-content" class="btn btn-primary btn-block m-auto">Login</button>
  </form>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'LoginForm',
        data() {
            return {
                user_name: '',
                password: '',
            }
        },
        methods: {
            async handleSubmit() {
                const response = await axios.post('login', {
                    user_name: this.user_name,
                    password: this.password
                });

                console.log(response);
                localStorage.setItem('token', response.data.token);
                this.$store.dispatch('user', response.data.user);
                this.$router.push('/');
            }
        },
    }
</script>