<template>
  <section class="jumbotron">
    <h3 class="jumbotron-heading">Search Github Users</h3>
    <div>
      <input
        type="text"
        placeholder="enter the name you search"
        v-model="keyWord"
      />&nbsp;<button @click="searchuser">Search</button>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "Search",
  data() {
    return {
      keyWord: "",
    };
  },
  methods: {
    searchuser() {
      this.$bus.$emit("updataListdata", {
        isFirst: false,
        isLoading: false,
        errMsg: "",
        uesrs: [],
      });
      axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
        (response) => {
          console.log("请求成功了", response.data.items);

          this.$bus.$emit("updataListdata", {
            isLoading: false,
            errMsg: "",
            uesrs: response.data.items,
          });
        },
        (error) => {
          console.log("请求失败了", error.message);
          this.$bus.$emit("updataListdata", {
            isLoading: false,
            errMsg: "error.message",
            uesrs: [],
          });
        }
      );
    },
  },
  mounted() {},
};
</script>

<style>
</style>