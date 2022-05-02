<template>
  <div class="row">
    <!-- 展示用户列表 -->
    <div
      v-show="info.uesrs.length"
      class="card"
      v-for="user in info.uesrs"
      :key="user.logoin"
    >
      <a :href="user.html_url" target="_blank">
        <img :src="user.avatar_url" style="width: 100px" />
      </a>
      <p class="card-text">{{ user.login }}</p>
    </div>
    <!-- 展示欢迎词 -->
    <h1 v-show="info.isFirst">欢迎您使用!</h1>
    <!-- 展示加载中 -->
    <h1 v-show="info.isLoading">加载中。。。</h1>
    <!-- 展示错误信息 -->
    <h1 v-show="info.errMsg">{{ info.errMsg }}</h1>
  </div>
</template>

<script>
export default {
  name: "List",
  data() {
    return {
      info: {
        isFirst: true, //欢迎词
        isLoading: false, //加载中
        errMsg: "", //错误信息
        uesrs: [],
      },
    };
  },

  mounted() {
    this.$bus.$on("updataListdata", (dataObj) => {
      /*  this.isFirst = isFirst;
      this.isLoading = isLoading;
      this.errMsg = errMsg;
      this.uesrs = users; */
      this.info = { ...this.info, ...dataObj };
    });
  },
};
</script>

<style>
</style>