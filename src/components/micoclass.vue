<template>
  <div class="micoclass">
    <video :src="srcs" controls="controls"></video>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    data(){
      return {
        srcs: ''
      }
    },
    created(){
      document.body.style.backgroundColor = 'white'
    }
  }
</script>

<style lang="stylus" type="text/stylus">
  .micoclass
    margin 20px auto
    width 100%
    text-align center
    video
      height 300px
      width 90%
</style>
