<template>
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" v-model="firstName" placeholder="Enter First Name" />
    <input type="text" v-model="lastName" placeholder="Enter Last Name" />
    <input type="text" v-model="userName" placeholder="Enter User Name" />
    <input type="text" v-model="email" placeholder="Enter Email" />
    <input type="password" v-model="password" placeholder="Enter Password" />
    <button v-on:click="signUp">Sign Up</button>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: "SignUp",
  
  data() {
    return {
      firstName: "",
      lastName: "",
      userName: "",
      email: "",
      password: "",
    };
  },

  methods: {
    async signUp() {
      console.warn('signUp', this.firstName, this.lastName, this.userName, this.email, this.password)
      
      let result = await axios.post("http://127.0.0.1:8000/register/", {
        username: this.userName, 
        password: this.password, 
        email: this.email, 
        first_name: this.firstName, 
        last_name: this.lastName
      });

      console.warn(result);
    },
  },
};
</script>

<style>
.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid skyblue;
}
.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: #fff;
  cursor: pointer;
}
</style>