<template>
  <form class="form-wrapper">
    <div class="info">欢迎登录</div>
    <div class="form-input">
      <label>登录名</label>
      <input type="text" v-model="name">
    </div>
    <div class="form-input">
      <label>密码</label>
      <input type="password" v-model="password">
    </div>
    <div class="btns">
      <button type="button" @click="submit()">登录</button>
      <button type="button" @click="()=>{this.$router.push({'name':'reg'})}">注册</button>
    </div>
  </form>
</template>

<script>
  export default {
    name: 'Login',
    data () {
      return {
        name: '',
        password: ''
      }
    },
    methods: {
      submit () {
        if (this.name.trim() === '') {
          alert('请输入登录名')
          return
        }
        if (this.password.trim() === '') {
          alert('请输入密码')
          return
        }
        if (localStorage.getItem('name') === this.name && localStorage.getItem('password') === this.password) {
          this.name = ''
          this.password = ''
          this.$router.push({ name: 'list' })
        } else {
          alert('登录失败，请检查用户名与密码')
        }
      }
    }
  }
</script>

<style scoped>
  .info {
    padding: 30px;
    font-size: 18px;
    font-weight: bold;
    text-align: center;
  }
</style>
