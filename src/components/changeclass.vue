<template>
<div class="changeclass">
  <li v-for="(i,index) in changeclass" class="changeclass-part">{{i.changeinfo}}</li>
</div>
</template>

<script type="text/ecmascript-6">
  export default{
    props: ['datas'],
    data(){
      return {
        changeclass: this.datas.changeclass
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus" scoped>
  .changeclass
    width 90%
    margin 10px auto 0
    .changeclass-part
      line-height 20px
      font-size 12px
      background-color rgba(7,17,27,0.1)
      margin-bottom 16px
      padding 6px 10px
      border-radius 8px
</style>
