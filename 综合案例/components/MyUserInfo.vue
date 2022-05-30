<template>
  <div>
    商品列表
    <MyTable>
      <template #tr>
        <tr v-for="(item, index) in data" :key="item.id">
          <td>{{ index + 1 }}</td>
          <td>{{ item.goods_name }}</td>
          <td>￥{{ item.goods_price }}</td>
          <td>
            <button
              v-if="item.inputVisible"
              class="btn btn-primary btn-sm add-tag"
              @click="fn(item.id)"
            >
              +Tag
            </button>
            <input
              type="text"
              v-else
              class="tag-input form-control"
              v-focus
              @keyup.enter="up(item, $event)"
              @keyup.esc="esc"
            />
            <span
              v-for="tag in item.tags"
              :key="tag"
              class="badge badge-warning"
              >>{{ tag }}</span
            >
          </td>
          <td>
            <button class="btn btn-danger btn-sm" @click="del(item.id)">
              删除
            </button>
          </td>
        </tr>
      </template>
    </MyTable>
  </div>
</template>

<script>
import MyTable from './MyTable.vue'
// import axios from 'axios'
export default {
  components: { MyTable },
  data() {
    return {
      data: [
        {
          goods_name: '精美女装',
          goods_price: 298,
          id: 1,
          inputValue: '',
          inputVisible: true,
          tags: ['时尚', '潮流']
        },
        {
          goods_name: '时尚男装',
          goods_price: 188,
          id: 2,
          inputValue: '',
          inputVisible: true,
          tags: ['时尚', '潮流']
        },
        {
          goods_name: '可爱童装',
          goods_price: 99,
          id: 3,
          inputValue: '',
          inputVisible: true,
          tags: ['可爱', '便宜']
        }
      ]
    }
  },
  methods: {
    del(id) {
      this.data = this.data.filter((item) => item.id !== id)
    },
    fn(id) {
      const obj = this.data.find((item) => item.id === id)
      obj.inputVisible = false
    },
    up(item, e) {
      if (e.target.value.trim() === '') return
      item.tags.push(e.target.value)
      item.inputVisible = true
    },
    esc(e) {
      e.target.value = ''
    }
  }
}
</script>

<style>
.badge {
  margin-right: 5px;
}
</style>
