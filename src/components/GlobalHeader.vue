<template>
  <nav class="navbar bg-primary" data-bs-theme="dark">
    <a class="navbar-brand" href="#">者也专栏</a>
    <ul v-if="!user.isLogin" class="list-inline mb-0">
      <li class="list-inline-item"><a href="#" class="btn btn-outline-light my-2">登录</a></li>
      <li class="list-inline-item"><a href="#" class="btn btn-outline-light my-2">注册</a></li>
    </ul>
    <ul v-else>
      <li class="list-inline-item">
        <DropDown :title="`你好，${user.name}`">
          <DropdownItem><a href="#" class="dropdown-item">新建文章</a></DropdownItem>
          <DropdownItem><a href="#" class="dropdown-item">编辑资料</a></DropdownItem>
          <DropdownItem><a href="#" class="dropdown-item">退出登录</a></DropdownItem>
        </DropDown>
      </li>
    </ul>
  </nav>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue'
import DropDown from './DropDown.vue'
import DropdownItem from './DropdownItem.vue'
export interface UserProps {
  isLogin: boolean;
  name?: string;
  id?: number;
}

export default defineComponent({
  name: 'GlobalHeader',
  components: {
    DropDown,
    DropdownItem
  },
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true
    }
  }
})
</script>

<style lang="less" scoped>
</style>
