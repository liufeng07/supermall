<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
    <FeatureView/>
    <TabControl class="tab-control" :titles="['流行', '新款', '精选']"/>
    <goods-list :goods="goods['pop'].list"/>
  </div>
</template>

<script>
//面向对象开发
import {getHomeMultidata, getHomeGoods} from "@/network/home";
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import FeatureView from "./childComps/FeatureView";
import GoodsList from "@/components/content/goods/GoodsList";

//公共组件
import NavBar from "@/components/common/navbar/NavBar";
import TabControl from "@/components/content/tabControl/TabControl";


export default {
  name: "Home",
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,
    GoodsList,

    NavBar,
    TabControl
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        'pop': {page: 0, list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []},
      },
    }
  },
  created() {
    //1.请求多个数据
    this.getHomeMultidata();
    //2.请求商品数据
    this.getHomeGoods('pop');//请求流行数据
    this.getHomeGoods('new');//请求新款数据
    this.getHomeGoods('sell');//请求精选数据
  },
  //网络请求相关方法
  methods: {
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        //let result = JSON.stringify(res);
        //console.log("getHomeMultidata:" + result);
        // 保存到result变量中
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type, page).then(res => {
        //接口更改
        //let result = JSON.stringify(res);
        //console.log("getHomeGoods:" + result);
        //push(...将集合数据遍历放入集合中)
        this.goods[type].list.push(...res.data.list)
        //页码增加
        this.goods[type].page += 1
      })
    }
  }
}
</script>

<style scoped>
#home {
  padding-top: 44px;
}

.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0px;
  right: 0px;
  top: 0px;
  z-index: 9;
}

/*滑动固定 */
.tab-control {
  position: sticky;
  top: 44px;
  /*防止商品数据覆盖tabbar 加层级*/
  z-index: 9;
}

</style>
