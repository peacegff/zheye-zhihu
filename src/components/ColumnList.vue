<template>
  <div class="row">
    <div class="col-4 mb-4" v-for="column in columnList" :key="column.id">
      <div class="card h-100 shadow-sm">
        <div class="card-body text-center">
          <img :src="column.avatar" class="rounded-circle border border-light w-25 my-3" :alt="column.title">
          <h5 class="card-title">{{column.title}}</h5>
          <p class="card-text" text-left>{{column.description}}</p>
          <a href="#" class="btn btn-outline-primary">进入专栏</a>
       </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from 'vue'
export interface ColumnProps {
  id: number;
  title: string;
  avatar?: string;
  description: string;
}

export default defineComponent({
  name: 'ColumnList',
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>,
      required: true
    }
  },
  setup (props) {
    const columnList = computed(() => {
      return props.list.map(column => {
        if (!column.avatar) {
          column.avatar = require('@/assets/avatar.jpg')
        }
        return column
      })
    })
    return {
      columnList
    }
  }
})
</script>

<style lang="less" scoped>
</style>
