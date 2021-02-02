<template>
  <!--  遍历商品数据-->
  <div class="goods">
  <!--  商品详情子组件-->
    <goods-list-item v-for="item in goods" :goods-item="item"></goods-list-item>
  </div>
</template>

<script>

import GoodsListItem from "./GoodsListItem";

export default {
  name: "GoodsList",
  props: {
    // 从home拿到商品数据
    goods: {
      type: Array,
      default: []
    }
  },
  components: {
    GoodsListItem
  }
}
</script>

<style scoped>
.goods {
  /*水平布局*/
  display: flex;
  /*让弹性盒元素在必要的时候拆行*/
  flex-wrap: wrap;
  /*均等份*/
  justify-content: space-around;
  padding: 2px;
}
</style>