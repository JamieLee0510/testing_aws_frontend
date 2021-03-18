<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>{{ message }}</h1>
    <button @click="testing">testing</button>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      message: "",
      API_URL:
        "http://testnode-env.eba-s5cqe8ci.us-east-2.elasticbeanstalk.com/api/testing",
    };
  },
  methods: {
    async testing() {
      await axios.get(this.API_URL).then((res) => {
        this.message = res.data.message;
      });
    },
  },
  components: {
    HelloWorld,
  },
};
</script>
