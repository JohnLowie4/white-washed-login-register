<template>
  <div class="backdrop" @click.self="closePage">
    <form @submit.prevent="handleSubmit">
      <label>Email:</label>
      <input type="email" required v-model="email">

      <label>Password:</label>
      <input type="password" required v-model="password">

      <label>Confirm Password:</label>
      <input type="password" required v-model="confirmPassword">
      <div v-if="passwordError" class="error">{{ passwordError}}</div>

      <div class="terms">
        <input type="checkbox" v-model="newsLetter">
        <label>Receive news letters and promotions</label>
      </div>

      <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept terms and conditions</label>
      </div>

      <div class="submit">
        <button>Create Account</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      confirmPassword: "",
      terms: false,
      passwordError: "",
      newsLetter: false
    }
  },
  methods: {
    handleSubmit() {
      if (this.password !== this.confirmPassword) {
        this.passwordError = "Password match failed"
      } else {
        this.email = "";
        this.password = "";
        this.confirmPassword = "";
        this.terms = false;
        this.passwordError = "";
        this.newsLetter = false;
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
    color: #2a3b45;
  }
  .backdrop {
    top:0;
    position: fixed;
    background: #3b3c3e;
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
    color: #acacac;
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
    border-bottom: 1px solid #727377;
    color: #3b3c3e;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top:2px;
  }
  button {
    background: #3b3c3e;
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
    color: #3b3c3e;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }

</style>