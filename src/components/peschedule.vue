<template>
<div class="peschedule">
  <div class="peschedule-title">
    <div class="title-item">课程名称</div>
    <div class="title-item">上课时间</div>
    <div class="title-item">任课老师</div>
    <div class="title-item">上课教室</div>
  </div>
  <div class="peschedule-text">
    <li v-for="(i,index) in stuinfo" class="peschedule-all">
      <span class="stuinfo-part">{{i.name}}</span>
      <span class="stuinfo-part">{{i.time}}</span>
      <span class="stuinfo-part">{{i.teacher}}</span>
      <span class="stuinfo-part">{{i.place}}</span>
    </li>
  </div>
</div>
</template>

<script type="text/ecmascript-6">
  export default{
    props: ['datas'],
    data(){
      return {
        stuinfo: this.datas.peschedule
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus" scoped>
  .peschedule-title
    background-color rgba(7, 17, 27, 0.07)
    margin 6px 0
    width 100%
    display flex
    .title-item
      flex 1
      padding 8px 0
      text-align center
      font-size 14px

  .peschedule-all
    display flex
    .stuinfo-part
      flex 1
      text-align center
      padding 8px
      font-size 12px
</style>
