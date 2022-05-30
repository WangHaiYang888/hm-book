<template>
  <div class="app">
    <MyHeader>
      <template #heater> <h2>购物车案例</h2></template>
    </MyHeader>
    <MyTabBar
      :tabList="tabList"
      :active="active"
      @changeTab="changeTab"
    ></MyTabBar>
    <keep-alive><component :is="comName" /></keep-alive>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import MyHeader from './components/MyHeater.vue'
import MyTabBar from './components/MyTabBar.vue'
import MyGoodsList from './components/MyGoodsList.vue'
import MyGoodsSearch from './components/MyGoodsSearch.vue'
import MyUserInfo from './components/MyUserInfo.vue'
export default {
  components: { MyHeader, MyTabBar, MyGoodsList, MyGoodsSearch, MyUserInfo },
  data() {
    return {
      // tab栏的数据
      tabList: [
        { icon: 'icon-shangpinliebiao', title: '商品列表', name: 'MyUserInfo' },
        { icon: 'icon-sousuo', title: '商品搜索', name: 'MyGoodsList' },
        { icon: 'icon-user', title: '用户中心', name: 'MyGoodsSearch' }
      ],
      active: 0
      // comName: 'MyUserInfo'
    }
  },
  methods: {
    changeTab(val) {
      this.active = val
    }
  },
  computed: {
    comName() {
      return this.tabList[this.active].name
    }
  }
}
</script>

<style>
.app {
  padding: 50px 0;
}
</style>
