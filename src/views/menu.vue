<template>
  <div class="my-tab-bar">
    <div
      class="tab-item"
      v-for="(item, index) in tabs"
      :key="index"
      @click="tabClickFn(index)"
      :class="{ current: activeIndex === index }"
    >
      <!-- 图标 -->
      <span class="iconfont" :class="item.icon"></span>
      <!-- 文字 -->
      <span>{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tabs: {
      type: Array,
      default: () => [],
      required: true,
    },
  },
  data() {
    return {
      activeIndex: 0,
    };
  },
  methods: {
    tabClickFn(n) {
      this.activeIndex = n;
      this.$emit('changeCom',n)
    },
  },
};
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .current {
  color: #1d7bff;
}
}
</style>
