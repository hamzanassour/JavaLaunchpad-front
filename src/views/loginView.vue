<template>
  <div>
    <h1>Login</h1>
    <form @submit.prevent="login">
      <div>
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" />
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" />
      </div>
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
import qs from "qs";
export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    login() {
      const credentials = {
        username: this.username,
        password: this.password,
      };
      const data = qs.stringify(credentials);
      const headers = {
        "Content-Type": "application/x-www-form-urlencoded",
      };
      axios
        .post("http://localhost:9090/login", data, { headers })
        .then(() => {
          // Successful login, redirect the user to the inbox page
          console.log("logged in ");
        })
        .catch(() => {
          // Login failed, display an error message to the user
          alert("Login failed. Please try again.");
        });
    },
  },
};
</script>
