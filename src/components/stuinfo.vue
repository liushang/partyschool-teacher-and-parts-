<template>
  <div class="stuinfo">
    <div class="stuinfo-title">
      <div class="title-item">姓名</div>
      <div class="title-item">性别</div>
      <div class="title-item">学号</div>
    </div>
    <div class="stuinfo-text">
      <li v-for="(i,index) in stuinfo" class="stuinfo-all" @click="checkstu(index)">
        <span class="stuinfo-part">{{index+1}}.{{i.name}}</span>
        <span class="stuinfo-part">{{i.sex}}</span>
        <span class="stuinfo-part">{{i.id}}</span>
      </li>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    props: ['datas'],
    data(){
      return {
        stuinfo: this.datas.stuinfo
      }
    },
    methods: {
      checkstu(index){
        this.$emit('checksin', index)
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus" scoped>
  .stuinfo-title
    background-color rgba(7, 17, 27, 0.07)
    margin 6px 0
    width 100%
    display flex
    .title-item
      flex 1
      padding 8px 0
      text-align center
      font-size 14px

  .stuinfo-all
    display flex
    .stuinfo-part
      flex 1
      text-align center
      padding 8px
</style>
