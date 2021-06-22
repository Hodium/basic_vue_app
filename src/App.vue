<template>
  <div>
    <label>THIS IS A GOOD TEST</label>
    <label>API WORKS -> {{ apiresult }}</label>
    <br />
    <label>BUT THIS IS EVEN BETTER MOFO!!</label>
    <label>{{ otherApiResult }}</label>
    <br />
    <label>MON FICHEIRO</label>
    <label>{{ testFiles }}</label>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "App",
  data() {
    return {
      apiresult: "",
      testFiles: "",
    };
  },
  mounted() {
    Axios.get("/test").then((res) => {
      this.apiresult = res.data;
    });
    Axios.get("/anotherTest").then((res) => {
      this.otherApiResult = res.data;
    });
    Axios.post("/receive", { data: "aaaaaaaaaaaaaaaa" });
    var that = this;
    setTimeout(function () {
      Axios.post("/receive", { data: "bbbbbbbbbbbbbbbbbb" }).then((res) => {
        that.testFiles = res.data;
      });
    }, 10000);

    setTimeout(function () {
      Axios.delete("/delete").then((res) => {
        that.testFiles = res.data;
      });
    }, 20000);
  },
};
</script>

<style>
</style>