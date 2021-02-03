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
  mounted() {
    console.log(this.$refs.aaa); //undefined
    console.log(document.querySelector('.wrapper'));
    this.scroll = new BScroll(document.querySelector('.wrapper'), {})
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
