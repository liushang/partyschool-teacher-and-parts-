<template>
  <div class="activate">
    <div class="up">账号激活</div>
    <form action="">
      <div class="oldph"><input v-model="stuid" class="sty" type="text" placeholder="  工  号" required></div>
      <div class="text1"><input v-model="idcard" class="sty" type="text" placeholder="  身份证" required></div>
      <div class="conph"><input v-model="mobile" class="sty" type="text" placeholder="  手  机" required></div>
      <div class="text2"><input class="sty" type="text" placeholder="  验证码" required>
        <button class="text">获取验证码</button>
      </div>
      <router-link to="/setpassword">
        <div class="next" @click="activate">
          <input style="color: white;background-color: #8b0000" type="submit" value="下一步">
        </div>
      </router-link>
    </form>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    data(){
      return {
        stuid: '',
        idcard: '',
        mobile: '',
        textcode: ''
      }
    },
    created(){
      document.getElementsByClassName('header')[0].style.backgroundColor = 'rgb(89,95,111)'
    },
    methods: {
      activate(){
        window.localStorage.setItem('stuid', this.stuid)
        this.$parent.stuid = this.stuid
        window.localStorage.setItem('idcard', this.idcard)
        window.localStorage.setItem('mobile', this.mobile)
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus">
</style>
