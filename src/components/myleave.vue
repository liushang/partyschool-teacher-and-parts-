<template>
  <div class="mypuzzle" style="height: auto">
    <li v-for="(item, index1) in leave">
      <el-col :span="24">
        <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" theme="">
          <el-submenu index="1">
            <template slot="title">
              <span class="ltitle">{{item.time}}<span v-if="item.classnum">&nbsp;&nbsp; &nbsp; &nbsp;  第{{item.classnum}}节</span></span>
              <span>{{item.classname}}</span>
              <span class="rtitle">{{item.state}}</span>
            </template>
            <el-menu-item index="1-1" v-for="(per, index2) in item.leave"
                          @click="checkleave('/leavelist', index1, index2)" :key="1">
              <div class="ltitle">{{per.stuname}}</div>
              <div class="rtitle">{{per.state}}</div>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-col>
    </li>
    <div style="height: 50px;width: 100%;clear: both"></div>
    <!--<div class="havepuzzle" v-if="this.$parent.identity!=='t'">-->
    <!--<router-link to="/leavelist" style="color: white">-->
    <!--<div class="newpuzzle">我要请假</div>-->
    <!--</router-link>-->
    <!--</div>-->
  </div>
</template>

<script type="text/ecmascript-6">
  export default{
    data(){
      return {
        leave: [
          {
            'time': '2017-7-2',
            'ltime': '2017-7-2至2017-7-5',
            'day': '4',
            'reason': '家中有事',
            'state': '已批准'
          },
          {
            'time': '2017-6-5',
            'ltime': '2017-6-7至2017-6-9',
            'day': '3',
            'reason': '病假',
            'state': '待审核'
          },
          {
            'time': '2017-6-1',
            'ltime': '2017-6-2至2017-6-3',
            'day': '2',
            'reason': '同学结婚',
            'state': '未通过'
          },
          {
            'time': '2017-5-3',
            'ltime': '2017-5-4至2017-5-4',
            'day': '1',
            'reason': '家中有事',
            'state': '已批准'
          }
        ],
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
      this.leave = this.tleave
      document.body.style.backgroundColor = 'white'
    },
    methods: {
      checkleave(obj, index1, index2){
        this.$router.push({
          path: obj,
          query: {index1: index1, index2: index2}
        })
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus">
  @import '../common/css/myleave.styl'
</style>
