<template>
  <div class="home">
    <div>{{count}}</div>
    <button @click="increment()">증가</button><br>
    <input type="text" name="userId" v-model='state.form.userId'><br>
    <input type="password" name="userPw" v-model='state.form.userPw'><br>
    <button @click="submit()">로그인</button>
  </div>
</template>

<script lang="ts">
import router from '@/router'
import { reactive } from 'vue'

export default {
  data () {
    return {
      count: 0
    }
  },
  setup () {
    const state = reactive({
      form: {
        userId: '',
        userPw: ''
      }
    })

    const submit = () => {
      if (state.form.userId === '') {
        alert('ID를 입력해주새요')
        return false
      }
      if (state.form.userPw === '') {
        alert('PW를 입력해주새요')
        return false
      }
      router.push('/about')
      alert('로그인 되었습니다')
    }
    return { state, submit }
  },
  methods: {
    increment () {
      this.count++
    }
  }
}
</script>
