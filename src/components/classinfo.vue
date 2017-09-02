<template>
  <div class="partinfo">
    <headernull :something="sometext" @dosome="modify" ref="headersome"></headernull>
    <div class="partinfo-main">
      <div class="partinfo-top">
        <div class="topleft-name">
          <div class="name-class">
            <el-dropdown class="text-type" trigger="click" @command="handleCommand2">
      <span class="el-dropdown-link">
        {{classname}}<i class="el-icon-caret-bottom el-icon--right"></i>
      </span>
              <el-dropdown-menu slot="dropdown" style="font-size: 12px;width: 50px">
                <el-dropdown-item :command="i.classname" v-for="(i,index) in partinfo" style="text-align: center"
                                  :key="0">
                  {{i.classname}}
                </el-dropdown-item>
              </el-dropdown-menu>
            </el-dropdown>
          </div>
          <div class="name-message">
            <svg @click.stop="messageclass" class="icon"
                 aria-hidden="true">
              <use xlink:href="#icon-xiaoxifasong"></use>
            </svg>
          </div>
        </div>
        <div class="topright-name">
          <div class="nameone">
            <div class="name-part">班主任</div>
            <div class="name-name">
              <div  @click="checkstu(-1)">
                {{singleinfo.partone.detail.name}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit(index1)" class="icon partinfoicon"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
          <div class="nameone">
            <div class="name-part">学员数</div>
            <div class="name-name">
              <div>
                {{singleinfo.parttwo}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit2(index2)" class="icon partinfoicon"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
          <div class="nameone">
            <div class="name-part">开班时间</div>
            <div class="name-name">
              <div>
                {{singleinfo.partother}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit3(index3)" class="icon partinfoicon"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="partinfo-bottom">
        <div class="bottom-items">
          <router-link to="/classinfo/stuinfo" replace>学员信息</router-link>
        </div>
        <div class="bottom-items">
          <router-link to="/classinfo/schedule" replace>班级课表</router-link>
        </div>
        <div class="bottom-items">
          <router-link to="/classinfo/change" replace>调课信息</router-link>
        </div>
      </div>
      <router-view :datas="singleinfo" @checksin="checkstu"></router-view>
      <div class="partinfo-modal" @click="shutmodal">
        <li class="modal-li">
          <span class="modal-name">&nbsp;&nbsp;&nbsp;&nbsp;手机号&nbsp;<input
            class="partinfoinput" type="text" v-model="singeldetail.phone"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name"> 邮&nbsp;&nbsp;&nbsp;&nbsp;箱&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.email"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">姓&nbsp;&nbsp;&nbsp;&nbsp;名&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.name"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">职&nbsp;&nbsp;&nbsp;&nbsp;务&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.do"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">性&nbsp;&nbsp;&nbsp;&nbsp;别&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.sex"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">出生日期&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.sex"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">学&nbsp;&nbsp;&nbsp;&nbsp;历&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.state"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">毕业院校&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.sch"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">政治面貌&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.party"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">参加工作时间&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.time"></span></li>
      </div>
      <talkinput :talk="talktext" @talksub="subtalk" @changetalk="gettalk"></talkinput>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import headernull from '@/components/header/header-null'
  import talkinput from '@/components/talkinput/talkinput'
  export default{
    data(){
      return {
        talktext: '',
        sometext: '编辑',
        classname: '',
        singleinfo: '',
        singeldetail: '',
        partinfo: [{
          'classname': '9月一班',
          'partone': {
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          },
          'parttwo': 30,
          'partother': '2017-09-09',
          'stuinfo': [{
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'peschedule': [{
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }],
          'changeclass': [{'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}]
        }, {
          'classname': '9月二班',
          'partone': {
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          },
          'parttwo': 40,
          'partother': '2017-09-22',
          'stuinfo': [{
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'peschedule': [{
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }],
          'changeclass': [{'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}]
        }, {
          'classname': '9月三班',
          'partone': {
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          },
          'parttwo': 20,
          'partother': '2017-10-09',
          'stuinfo': [{
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'peschedule': [{
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }],
          'changeclass': [{'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}]
        }, {
          'classname': '9月四班',
          'partone': {
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          },
          'parttwo': 24,
          'partother': '2017-11-09',
          'stuinfo': [{
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'peschedule': [{
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }],
          'changeclass': [{'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}]
        }, {
          'classname': '9月五班',
          'partone': {
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          },
          'parttwo': 33,
          'partother': '2017-12-09',
          'stuinfo': [{
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '李四',
            'sex': '男',
            'id': '10111',
            'come': 1,
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '李四',
              'do': '学员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'peschedule': [{
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李四',
            'place': '勤学楼201'
          }, {'name': '毛泽东思想', 'time': '9.9-10.9 9:00-10:00', 'teacher': '李四', 'place': '勤学楼201'}, {
            'name': '毛泽东思想',
            'time': '9.9-10.9 9:00-10:00',
            'teacher': '李4',
            'place': '勤学楼201'
          }],
          'changeclass': [{'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}, {'changeinfo': '9-10 9:00-10:00 马克思主义哲学 李四老师 调整至 9:15 9:00-10:00 李思老师 勤学楼201上'}]
        }]
      }
    },
    created(){
      document.body.style.backgroundColor = 'white'
      this.classname = this.partinfo[0].classname
      this.singleinfo = this.partinfo[0]
    },
    mounted(){
      document.getElementsByClassName('talk-bottom')[0].style.display = 'none'
    },
    components: {
      headernull,
      talkinput
    },
    methods: {
      edit(index){
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon')[index].style.color = 'red'
        this.singeldetail = this.singleinfo.partone[index]
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
      },
      edit2(index){
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon')[index + this.singleinfo.partone.length].style.color = 'red'
        this.singeldetail = this.singleinfo.parttwo[index]
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
      },
      edit3(index){
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon')[index + this.singleinfo.partone.length + this.singleinfo.parttwo.length].style.color = 'red'
        this.singeldetail = this.singleinfo.partone[index]
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
      },
      modify(){
        if (this.$refs.headersome.sometext === '编辑') {
          this.$refs.headersome.sometext = '完成'
          for (let i of document.getElementsByClassName('partinfoicon')) {
            i.style.visibility = 'visible'
          }
        } else {
          this.$refs.headersome.sometext = '编辑'
          for (let i of document.getElementsByClassName('partinfoicon')) {
            i.style.color = 'black'
          }
          for (let i of document.getElementsByClassName('partinfoicon')) {
            i.style.visibility = 'hidden'
            document.getElementsByClassName('partinfo-modal')[0].style.bottom = '-100%'
          }
        }
      },
      handleCommand2(command){
        this.classname = command
        for (let i of this.partinfo) {
          if (i.classname === command) {
            this.singleinfo = i
          }
        }
        this.$router.push('/classinfo/stuinfo')
      },
      gettalk(msg){
        this.talktext = msg
      },
      subtalk(){
        document.getElementsByClassName('talk-bottom')[0].style.display = 'none'
        this.$message({
          message: '发送成功！',
          type: 'success',
          duration: 800
        })
      },
      checkstu(index){
        console.log(index)
        if (index === -1) {
          document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
          this.singeldetail = this.singleinfo.partone.detail
          console.log(this.singeldetail)
          return
        }
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
        this.singeldetail = this.singleinfo.stuinfo[index].detail
      },
      messageclass(){
        document.getElementsByClassName('talk-bottom')[0].style.display = 'block'
      },
      shutmodal(){
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '-100%'
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus" scoped>
  @import '../common/css/classinfo'
</style>
