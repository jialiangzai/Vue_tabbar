<template>
  <div class="my-header" :style="{backgroundColor:bgcolor}">{{title}}</div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: "tabbar 案例",
    },
    bgcolor: {
      type: String,
      default: "#1d7bff",
    },
  },
};
</script>

<style lang="less" scoped>
.my-header {
  height: 50px;
  line-height: 50px;
  text-align: center;
  font-size: 16px;
  background-color: red;
  color: #fff;
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
}
</style>
