<template>
  <div id="app">
    <School></School>
    <Student></Student>
    <h2>更改了代码</h2>
  </div>
</template>

<script>
import School from "./components/School.vue";
import Student from "./components/Student.vue";
export default {
  name: "App",
  components: {
    School,
    Student,
  },
};
</script>

<style>
#app {
  background-color: pink;
  padding: 30px;
}
</style>