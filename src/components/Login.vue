<template>
  <div class="container">
    <h1 class="text-center">Votes' App</h1>
    <form>
      <div class="form-group">
        <label for="username">Username</label>
        <input
          type="text"
          class="form-control"
          v-model="form.email"
          id="username"
          placeholder="name@example.com"
          required
        />
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" class="form-control" v-model="form.password" id="password" />
      </div>

      <button type="button" class="btn btn-primary" @click="login">Login</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",

  data() {
    return {
      form: {
        username: "",
        password: ""
      }
    };
  },

  methods: {
    login() {
      axios
        .post("http://localhost:49220/api/login/authenticate", this.form)
        .then(function(response) {
          localStorage.setItem("token", response.data);
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>

<style module>
</style>
