# InfiniteScroll
无限滚动，上拉加载更多的一个Vue2的指令实现。

提取自Element的功能， 修复了其中节流 delay 默认值设置无效的问题

**局部注册用法**

```vue
<template>
  <div>
    <div class="container"
         v-infinite-scroll="load"
         :infinite-scroll-delay="180"
         :infinite-scroll-disabled="false"
         :infinite-scroll-distance="50"
         :infinite-scroll-immediate="false">
      <div v-for="item in list"
           :key="item"
           class="child">{{item}}</div>
    </div>
  </div>
</template>
<script>
/* eslint-disable */
import XdInfiniteScroll from '@/directives/XdInfiniteScroll/index.js';
export default {
  name: 'InfiniteScroll',
  // mixins: [],
  // components: {},
  // props: {},
  data() {
    return {
      list: []
    };
  },
  // computed: {},
  directives: {
    InfiniteScroll: XdInfiniteScroll
  },
  // watch:{},
  created() {
    //   this.load()
  },
  // mounted() {},
  // beforeRouteEnter(to, from, next) { next(vm => {}) },
  // beforeRouteUpdate(to, from, next) {},
  // beforeRouteLeave(to, from, next) {},
  // beforeDestroy() {},
  // destroyed() {},
  methods: {
    load() {
      console.log('load');
      let index = this.list.length;
      for (let i = index; i < index + 10; i++) {
        this.list.push(i);
      }
    }
  }
};
</script>
<style scoped>
.container {
  width: 200px;
  height: 400px;
  overflow-y: auto;
}
.child {
  height: 50px;
  background-color: aquamarine;
}
.child:nth-child(2n) {
  background-color: brown;
}
</style>

```

**全局注册**

```js
import Vue from "vue"
import XdInfiniteScroll from '@/directives/XdInfiniteScroll/index.js';
Vue.use(XdInfiniteScroll)
// 用法指令变更为 v-xd-infinite-scroll="load"
// v-xd-infinite-scroll 主要是为了避免命名冲突。可自行下载代码自行修改名称
```

