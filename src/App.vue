<template>
  <div>
    <label>THIS IS A GOOD TEST</label>
    <label>API WORKS -> {{ apiresult }}</label>

    <label>BUT THIS IS EVEN BETTER MOFO!!</label>
    <label>{{ otherApiResult }}</label>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "App",
  data() {
    return {
      apiresult: "",
    };
  },
  mounted() {
    Axios.get("/test").then((res) => {
      this.apiresult = res.data;
    });
    Axios.get("/anotherTest").then((res) => {
      this.otherApiResult = res.data;
    });
  },
};
</script>

<style>
</style>