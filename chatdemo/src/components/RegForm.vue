<template>
  <form class="form-wrapper">
    <div class="info">请输入以下信息</div>
    <div class="form-input">
      <label>登录名</label>
      <input type="text" v-model="name">
    </div>
    <div class="form-input">
      <label>密码</label>
      <input type="password" v-model="password">
    </div>
    <div class="form-input">
      <label>再次密码</label>
      <input type="password" v-model="passwordRepeat">
    </div>
    <div class="btns">
      <button type="button" @click="reg()">确定</button>
      <button type="button" @click="()=>{this.$router.back()}">取消</button>
    </div>
  </form>
</template>

<script>
  export default {
    name: 'RegForm',
    data () {
      return {
        name: '',
        password: '',
        passwordRepeat: ''
      }
    },
    methods: {
      reg () {
        if (this.name.trim() === '') {
          alert('请输入登录名')
          return
        }
        if (this.password.trim() === '') {
          alert('请输入密码')
          return
        }
        if (this.passwordRepeat.trim() === '') {
          alert('请再次输入密码')
          return
        }

        if (this.password === this.passwordRepeat) {
          localStorage.setItem('name', this.name)
          localStorage.setItem('password', this.password)
          this.$router.push({ name: 'login' })
        } else {
          alert('请检查密码是否输入一致')
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
