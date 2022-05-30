<template>
  <div class="my-tab-bar">
    <div
      class="tab-item"
      :class="{ current: index === active }"
      v-for="(item, index) in tabList"
      :key="item.title"
      @click="changeTab(index)"
    >
      <span class="iconfont" :class="[item.icon]"></span>
      <span>{{ item.title }}</span>
    </div>
  </div>
</template>

<script>
import '../fonts/iconfont.css'
export default {
  props: {
    tabList: {
      type: Array,
      required: true,
      validator: (value) => {
        if (value < 2 && value > 5) {
          return false
        } else {
          return true
        }
      }
    },
    active: {
      type: Number,
      default: 0
    }
  },
  methods: {
    changeTab(val) {
      this.$emit('changeTab', val)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    .iconfont {
      font-size: 18px;
    }
  }
  .current {
    color: #1d7bff;
  }
}
</style>
