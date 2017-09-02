<template>
  <div class="leavelist">
    <div class="leavelist-title"><span class="list-text">请假人</span><span class="text-text">{{leave.stuname}}</span>
    </div>
    <div class="leavelist-title"><span class="list-text">请假类型</span><span class="text-text">{{leave.leavetype}}</span>
    </div>
    <div class="leavelist-title"><span class="list-text">请假时间</span><span class="text-text">{{leave.stime}}
</span> 至 <span class="text-text">{{leave.etime}}</span>
      <div class="text-type"></div>
    </div>
    <div class="leavelist-title"><span class="list-text">请假总长</span><span class="text-text"><span class="day-num">{{leave.day}}天</span></span>
      <div class="text-type"></div>
    </div>
    <div>
      <div class="list-text">请假原因:</div>
      <div name="" v-model="listreson">{{leave.reason}}</div>
    </div>
    <div class="leavelist-sub" v-if="leave.state==='未批准'" style="background-color: #8b0000">
      <router-link to="/person/myleave" style="color: white">批准</router-link>
    </div>
    <div class="leavelist-sub" v-else>
      <router-link to="/person/myleave" style="color: white">已批准</router-link>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    data(){
      return {
        listtype: '',
        listbegin: '',
        listend: '',
        listnum: '',
        listreson: '',
        leave: {},
        tleave: [
          {
            'time': '2017-6-26',
            'classname': '马克思主义',
            'classnum': '3',
            'leave': [
              {
                'stuname': '黄小娟',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '何鑫',
                'state': '已批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '胡杰',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              }
            ]
          },
          {
            'time': '2017-6-22',
            'classname': '马克思主义',
            'classnum': '3',
            'leave': [
              {
                'stuname': '黄小娟',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '何鑫',
                'state': '已批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '胡杰',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              }
            ]
          },
          {
            'time': '2017-6-16',
            'classname': '马克思主义',
            'classnum': '3',
            'leave': [
              {
                'stuname': '黄小娟',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '何鑫',
                'state': '已批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '胡杰',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              }
            ]
          },
          {
            'time': '2017-6-14',
            'classname': '马克思主义',
            'classnum': '3',
            'leave': [
              {
                'stuname': '黄小娟',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '何鑫',
                'state': '已批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              },
              {
                'stuname': '胡杰',
                'state': '未批准',
                'day': '1',
                'stime': '2017-6-27',
                'etime': '2017-6-28',
                'reason': '家中有事',
                'leavetype': '事假'
              }
            ]
          }
        ]
      }
    },
    created(){
      this.leave = this.tleave[this.$route.query.index1].leave[this.$route.query.index2]
      document.body.style.backgroundColor = 'white'
    },
    methods: {
      handleCommand(command) {
        this.listtype = command
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus">
  @import '../common/css/leavelist.styl'
</style>
