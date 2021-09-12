<template>

  <teleport to=".modals" v-if="modal === 'login'">
    <Login @close="closePage"/>
  </teleport>
  
  <teleport to=".modals" v-if="modal === 'register'">
    <Register @close="closePage"/>
  </teleport>

  <div class="home">
    <span class="login" @click="changePage('login')">
      <h1>Login</h1>
    </span>
    <span class="register" @click="changePage('register')">
      <h1>Register</h1>
    </span>
  </div>

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
    background: #eeeeee;
  }
  h1 {
    color: #2a3b45;
  }
  span {
    cursor: pointer;
  }
  .home {
    display: flex;
    justify-content: space-evenly;
  }

</style>
