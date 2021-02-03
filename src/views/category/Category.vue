<template>
  <div class="wrapper" ref="aaa">
    <ul class="content">
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
      <li>测试</li>
    </ul>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: "Category",
  data() {
    return {
      scroll: null
    }
  },
  //组件创建完调用,没有把模版挂载上去
  // created() {
  //   console.log(this.$refs.aaa); //undefined
  //   console.log(document.querySelector('.wrapper')); //null
  //   this.scroll = new BScroll(this.$refs.aaa,{
  //
  //   })
  // },
  //组件创建完调用
  mounted() {
    // console.log(this.$refs.aaa); //undefined
    // console.log(document.querySelector('.wrapper'));
    this.scroll = new BScroll(document.querySelector('.wrapper'), {
      probeType: 3,
      pullUpLoad: true
    })
    //监听事件类型 实时滚动的位置
    this.scroll.on('scroll', (position) => {
      console.log(position);
    })

    //上拉加载更多（默认只会监听一次）
    this.scroll.on('pullingUp', () => {
      console.log('上拉加载更多');
    })
  }
}
</script>


<style scoped>
.wrapper {
  height: 150px;
  background-color: red;
  /*原生滑动 css控制*/
  /*overflow: hidden;*/
  /*overflow-y: scroll;*/

  overflow: hidden;
}
</style>
