<template>
  <div class="main">
    <Head  />
    <!-- <List /> 切换动态组件 -->
    <keep-alive >
    <component :is="currComponent"></component>
    </keep-alive>
    <Menu :tabs="tabs" @changeCom="changeFn"/>
  </div>
</template>

<script>
import Head from "./views/head.vue";
import List from "./views/list.vue";
import Menu from "./views/menu.vue";
import Search from "./views/search.vue";
import My from "./views/my.vue";

export default {
  name: "App",
  data() {
    return {
      currComponent: 'List',
      tabs:[
            {
              icon: "icon-shangpinliebiao",
              text: "商品列表",
               name: "List",
            },
            {
              icon: "icon-sousuo",
              text: "商品搜索",
              name: "Search",
            },
            {
              icon: "icon-user",
              text: "我的信息",
              name: "My",
            },
          ],
    }
  },
  components: {
    Head,
    List,
    Menu,
    Search,
    My,
  },
  methods: {
    changeFn(n) {
      this.currComponent = this.tabs[n].name
    }
  },
};
</script>

<style>
.main {
  padding: 50px 0;
}
</style>
