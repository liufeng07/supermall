<template>
  <div class="tab-control">
    <div v-for="(item,index) in titles" :key="item" class="tab-control-item" :class="{active:index === currentIndex}"
         @click="itemClick(index)">
      <span>{{item}}</span>
    </div>
  </div>

</template>

<script>
export default {
  name: "TabControl",
  props: {
    titles: Array,
    default() {
      return []
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  methods: {
    itemClick(index) {
      this.currentIndex = index
    }
  }
}
</script>

<style scoped>
.tab-control {
  /*水平布局*/
  display: flex;
  text-align: center;
  height: 40px;
  line-height: 40px;
  font-size: 15px;
  background-color: #fff;
}

.tab-control-item {
  /*平分间隔*/
  flex: 1;
}

/*高度撑起来*/
.tab-control-item span {
  padding: 5px;
}

.active {
  /*css变量*/
  color: var(--color-high-text);
}

.active span {
  border-bottom: 3px solid var(--color-tint);
}

</style>