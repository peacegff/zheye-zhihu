<template>
  <div class="cntainer">
    <global-header :user="currentUser"></global-header>
    <!-- <ColumnList :list="list"></ColumnList> -->
    <validate-form @form-submit="formSubmit">
      <div class="mb-3">
        <label class="form-label">电子邮箱</label>
        <validate-input type="text" :rules="emailRules" v-model="emailVal">{{ emailVal }}</validate-input>
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <validate-input type="password" :rules="passwordRules" v-model="passwordVal"></validate-input>
      </div>
      <template #submit >
        <button type="submit" class="btn btn-danger">提交</button>
      </template>
    </validate-form>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import ValidateForm from './components/ValidateForm.vue'
const currentUser: UserProps = {
  isLogin: true,
  name: 'peave'
}

export default defineComponent({
  name: 'App',
  components: {
    // ColumnList,
    GlobalHeader,
    ValidateInput,
    ValidateForm
  },
  setup () {
    const emailVal = ref('paec')
    const emailRules: RulesProp = [
      { type: 'required', message: '邮箱不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱' }
    ]

    const passwordVal = ref('')
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' }
    ]

    const formSubmit = (res: boolean) => {
      console.log('123', res)
    }

    return {
      currentUser,
      emailRules,
      emailVal,
      passwordRules,
      passwordVal,
      formSubmit
    }
  }
})
</script>

<style lang="less">

</style>
