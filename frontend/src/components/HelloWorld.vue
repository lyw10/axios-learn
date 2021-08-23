<template>
  <div class="hello">
    hello!
    <input ref="userName" type="text" />
    <input ref="userPassword" type="text" />
    <button @click="post">submit</button>
  </div>
</template>

<script>
const axios = require("axios");
export default {
  name: "HelloWorld",
  props: {},
  methods: {
    post: function () {
      let username = this.$refs.userName.value;
      let password = this.$refs.userPassword.value;

      axios({
        method: "post",
        url: "/user/login",
        baseURL: "http://47.100.104.162:8000",
        data: {
          username,
          password,
        },
      })
        .then((res) => console.log(res))
        .catch((err) => console.error(err));
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
