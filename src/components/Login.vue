<template>
  <h1>Login</h1>
  <div class="login">
    <input type="text" v-model="userName" placeholder="Enter User Name" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="login">Login</button>
  </div>
</template>
<script>

import axios from 'axios'

export default {
  name: "Login",

  data() {
    return {
      userName: "",
      password: "",
    };
  },

  methods: {
    async login() {
      console.warn('signUp', this.firstName, this.lastName, this.userName, this.email, this.password)
      
      let result = await axios.post("http://127.0.0.1:8000/login/", {
        username: this.userName, 
        password: this.password
      });

      console.warn(result);
    },
  },
};
</script>

<style>
.login input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid skyblue;
}
.login button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: #fff;
  cursor: pointer;
}

</style>