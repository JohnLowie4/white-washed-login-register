<template>

  <teleport to=".modals" v-if="modal === 'login'">
    <Login @close="closePage"/>
  </teleport>
  
  <!-- <teleport to=".modals" v-if="modal === 'register'">
    <Register />
  </teleport> -->

  <span @click="changePage('login')">
    <h1>Login</h1>
  </span>
  <span @click="changePage('register')">
    <h1>Register</h1>
  </span>

</template>

<script>
import Login from './components/Login.vue';
import Register from './components/Register.vue';

export default {
  name: 'App',
  components: {
    Login,
    Register
  },
  data() {
    return {
      modal: "",
    }
  },
  methods: {
    changePage(page) {
      this.modal = page;
    },
    closePage() {
      this.modal = "";
    }
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
  body {
    margin: 0;
    background: #eee;
  }
  h1 {
    color: rgb(90, 90, 90);
  }
  span {
    cursor: pointer;
  }
</style>
