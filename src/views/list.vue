
<template>
  <div>
    <Tb :goodsList="goodsList">
      <template v-slot:header>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>
      <!-- <template #body>
        <td>1</td>
        <td>xxx</td>
        <td>¥ 99.00</td>
        <td>xxx</td>
        <td>
          <button class="btn btn-danger btn-sm">删除</button>
        </td>
      </template> -->
      <template #body="{rom,index}">
        <td>  {{rom.id}} </td>
        <td>  {{rom.goods_name}} </td>
        <td>  {{rom.goods_price}} </td>
        <!-- 把单元格里的标签, tags徽章铺设下 -->
        <!-- <td>  {{rom.tags}} </td> 数组-->
        <td class="my-goods-list"> <span v-for="(itd) in rom.tags" :key="itd" class="badge btn-warning btn-sm">{{itd}}</span> </td>
        <td><button @click="delFn(index)" class="btn btn-danger btn-sm">删除</button></td>
      </template>
    </Tb>
  </div>
</template>

<script>
export default {
  created() {
    this.getGoodsList();
  },
  data() {
    return {
      goodsList: [],
    };
  },
  methods: {
    async getGoodsList() {
      const {
        data: { data, status },
      } = await this.$axios({
        url: "/api/goods",
      });
      console.log(data);
      if (status !== 0) return console.log("获取商品列表失败");
      this.goodsList = data;
    },
    delFn(ix){
      this.goodsList.splice(ix,1)
    }
  },
};
</script>

<style lang="less" scoped>
.my-goods-list {
  .badge {
    margin-right: 10px;
  }
}
</style>