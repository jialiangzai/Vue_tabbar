<template>
  <table class="table table-bordered table-stripped">
    <!-- 表格标题区域 -->
    <thead>
      <slot name="header"></slot>
    </thead>
    <!-- 表格主体区域 -->
    <tbody>
      <!-- 1. 提高组件复用性, 把表格列标题thead部分预留<slot>标签, 设置name属性
2. 使用MyTable.vue时, 传入自定义的列标题标签
3. 表格内容td部分也可以让组件使用者自定义, 也给tbody下tr内留好<slot>标签和name属性名
 -->
      <tr v-for="(item,index) in goodsList" :key="item.id">
        <!-- 使用插槽技术, 给MyTable.vue组件, 自定义列标题, 自定义表格内容 -->
        <!-- <td>  {{goodsList.id}} </td>
        <td>  {{goodsList.goods_name}} </td>
        <td>  {{goodsList.goods_price}} </td>
        <td>  {{goodsList.tags}} </td>
        <td><button class="btn btn-danger btn-sm">删除</button></td> -->
        <slot name="body" :rom = item :index=index></slot>
        <!-- 在传入标签时, 要使用对应组件内的数据 -->
        <!-- 1. 子MyTable.vue里在slot上绑定动态属性和值 
        2.父-MyGoodsList.vue在template上声明变量接收 
        3.插槽td标签上使用MyTable.vue内的数据 -->
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: "tables",
  props: {
    goodsList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
