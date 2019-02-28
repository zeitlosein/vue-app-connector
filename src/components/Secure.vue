<template>
  <div>
    <h1>Authorized Secure Page</h1>
    {{user}}
  </div>
</template>



<script>
import axios from "axios";

export default {
  // computed: {
  //   isLoggedIn: function() {
  //     return this.$store.getters.isLoggedIn;
  //   }
  // },
  // created: function() {
  //   this.$http.interceptors.response.use(undefined, function(err) {
  //     return new Promise(function(resolve, reject) {
  //       if (err.status === 401 && err.config && !err.config.__isRetryRequest) {
  //         this.$store.dispatch(user);
  //       }
  //       throw err;
  //     });
  //   });
  // },
  data() {
    return {
      user: []
    };
  },
  mounted() {
    getUser();
    {
      axios
        .get("https://api.getrunner.io/v3/runner/users/")
        .then(response => (this.user = response));
      // return this.$store.getters.isLoggedIn;
      // this.$http.interceptors.response.use(undefined, function(err) {
      //   return new Promise(function(resolve, reject) {
      //     if (err.status === 401 && err.config && !err.config.__isRetryRequest) {
      //       this.$store.dispatch(user);
      //     }
      //     throw err;
      //   });
      // });
    }
  }
};
</script>
