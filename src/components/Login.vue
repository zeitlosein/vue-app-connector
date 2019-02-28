<template>
  <div>
    <form class="login" @submit.prevent="login">
      <h1 class="login-signin-heading">Sign in</h1>

      <div>
        <label>Email</label>
        <input required v-model="email" type="text" placeholder="Nikolas@getrunner.io">
      </div>

      <div>
        <label>Password</label>
        <input required v-model="password" type="password" placeholder="password">
      </div>
      <hr>
      <button type="submit">Login</button>
    </form>
  </div>
</template>






<script>
export default {
  data() {
    return {
      email: "nikolas@getrunner.io",
      password: "password"
    };
  },
  methods: {
    login: function() {
      let email = this.email;
      let password = this.password;
      this.$store
        .dispatch("login", { email, password })
        .then(() => this.$router.push("/"))
        .catch(err => console.log(err));
    }
  }
};
</script>

<style lang="css">
body {
  background: #e2e2e2;
}

.login-wrapper {
  background: #fff;
  width: 70%;
  margin: 12% auto;
}

.login {
  max-width: 330px;
  padding: 10% 15px;
  margin: 0 auto;
}
.login .login-signin-heading,
.login .checkbox {
  margin-bottom: 10px;
}
.login .checkbox {
  font-weight: normal;
}
.login .login-control {
  position: relative;
  height: auto;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  padding: 10px;
  font-size: 16px;
}
.login .login-control:focus {
  z-index: 2;
}
.login label[type="text"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.login label[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>