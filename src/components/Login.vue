<template>
  <div class="backdrop" @click.self="closePage">
    <form @submit.prevent="handleSubmit">
      <label>Email:</label>
      <input type="email" required v-model="email">
      <div v-if="emailError" class="error">{{ emailError}}</div>

      <label>Password:</label>
      <input type="password" required v-model="password">
      <div v-if="passwordError" class="error">{{ passwordError}}</div>

      <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept terms and conditions</label>
      </div>

      <div class="submit">
        <button>Login</button>
      </div>
    </form>
  </div>
</template>

<script>
import db from '../static/db';

export default {
  data() {
    return {
      email: "",
      password: "",
      terms: false,
      emailError: "",
      passwordError: "",
      db: db
    }
  },
  methods: {
    handleSubmit() {
      if (this.email !== this.db.email) {
        this.emailError = "User with this email does not exist";
      }
      if (this.password !== this.db.password) {
        this.passwordError = "Email or password is incorrect"
      }
      if (this.email === this.db.email && this.password === this.db.password) {
        this.email = "";
        this.password = "";
        this.emailError = "";
        this.passwordError = "";
        this.terms = false;
      }
    },
    closePage() {
      this.$emit('close');
    }
  }
}
</script>

<style>
  template {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #2c3e50;
  }
  .backdrop {
    top:0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }
  form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding:40px;
    border-radius: 10px;
  }
  label {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top:2px;
  }
  button {
    background: #3f3f3f;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
    font-weight: bold;
    text-transform: uppercase;
    cursor: pointer;
  }
  .submit {
    text-align: center;
  }
  .error {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    color: #3f3f3f;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }

</style>