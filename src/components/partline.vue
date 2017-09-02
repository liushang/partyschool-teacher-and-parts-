<template>
  <div class="partinfo">
    <headersome :something="sometext" @dosome="modify" ref="headersome"></headersome>
    <div class="partinfo-main">
      <div class="partinfo-top">
        <div class="topleft-name">
          <el-dropdown class="text-type" trigger="click" @command="handleCommand2">
      <span class="el-dropdown-link">
        {{partname}}<i class="el-icon-caret-bottom el-icon--right"></i>
      </span>
            <el-dropdown-menu slot="dropdown" style="font-size: 12px;width: 50px">
              <el-dropdown-item :command="i.partname" v-for="(i,index) in partinfo" style="text-align: center" :key="0">
                {{i.partname}}
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </div>
        <div class="topright-name">
          <div class="nameone" v-if="singleinfo.partone">
            <div class="name-part">部长</div>
            <div class="name-name">
              <div v-for="(i1,index1) in singleinfo.partone">
                {{i1.detail.name}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit(index1)" class="icon partinfoicon1 partinfoicon"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
          <div class="nameone" v-if="singleinfo.parttwo">
            <div class="name-part">副部长</div>
            <div class="name-name">
              <div v-for="(i2,index2) in singleinfo.parttwo">
                {{i2.detail.name}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit2(index2)" class="icon partinfoicon partinfoicon2"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
          <div class="nameone" v-if="singleinfo.partother">
            <div class="name-part">其他</div>
            <div class="name-name">
              <div v-for="(i3,index3) in singleinfo.partother">
                {{i3.detail.name}}&nbsp;&nbsp;&nbsp;
                <svg @click.stop="edit3(index3)" class="icon partinfoicon partinfoicon3"
                     aria-hidden="true">
                  <use xlink:href="#icon-xie"></use>
                </svg>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="partinfo-bottom">
        <div class="bottom-title">部门职能</div>
        <div class="bottom-contain">
          {{singleinfo.partfunc}}
        </div>
      </div>
      <div class="partinfo-modal">
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;
          <!--<svg class="icon" style="background-color: #83dede;border-radius: 50%" aria-hidden="true">-->
          <!--<use xlink:href="#icon-gouwu&#45;&#45;copy"></use>-->
          <!--</svg>-->
          <span class="modal-name"> 手机号&nbsp;<input
            class="partinfoinput" type="text" v-model="singeldetail.phone"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;
          <!--<svg class="icon" style="background-color: #83dede;border-radius: 50%" aria-hidden="true">-->
          <!--<use xlink:href="#icon-gouwu&#45;&#45;copy"></use>-->
          <!--</svg>-->
          <span class="modal-name"> 邮&nbsp;&nbsp;&nbsp;&nbsp;箱&nbsp;<input
            class="partinfoinput" type="text" v-model="singeldetail.email"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">姓&nbsp;&nbsp;&nbsp;&nbsp;名&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.name"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">职&nbsp;&nbsp;&nbsp;&nbsp;务&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.do"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">性&nbsp;&nbsp;&nbsp;&nbsp;别&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.sex"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">出生日期&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.birth"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">学&nbsp;&nbsp;&nbsp;&nbsp;历&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.state"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">毕业院校&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.sch"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">政治面貌&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.party"></span></li>
        <li class="modal-li">&nbsp;&nbsp;&nbsp;&nbsp;<span class="modal-name">参加工作时间&nbsp;<input
          class="partinfoinput" type="text" v-model="singeldetail.time"></span></li>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import headersome from '@/components/header/header-some'
  export default{
    data(){
      return {
        sometext: '编辑',
        partname: '',
        singleinfo: '',
        singeldetail: '',
        partinfo: [{
          'partname': '教务处',
          'partfunc': '教务处（有的学校也称为教务部，如北大）是学校等教育机构的教学管理机构，主管各教师的教课任务、目标、进度及计划，学生的学习要求、目标、计划及考试等教与学各方面的事务，是学校的主要机构之一。该机构的负责人为教务处长（或教务长，也有的叫教导主任）。',
          'partone': [{
            'name': '张1',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'parttwo': [{
            'name': '李四',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '王五',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'partother': [{
            'name': '甲',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '乙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丁',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }]
        }, {
          'partname': '校领导',
          'partfunc': '校领导是指在学校中负有最高决策责任的管理人员，主要是指校长。校长首先是教育战略家，其特征是具有个性化的办学思想与思路，有较强的成就欲望，追求开拓和创新；其次校长作为联系上级与学校工作的中介，应具有较强的理解和执行上级方针政策、协调与上级关系的能力。最后校长既要娴熟地把握学校这个基层教育组织全部复杂工作，又要学会放权，既能够较为超脱地从整体上运筹帷幄，又能调动下属的积极性，把每一方面的工作能够全面而周到的安排。',
          'parttwo': [{
            'name': '李四',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '王五',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'partother': [{
            'name': '甲',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '乙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丁',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }]
        }, {
          'partname': '办公室',
          'partfunc': '教务处（有的学校也称为教务部，如北大）是学校等教育机构的教学管理机构，主管各教师的教课任务、目标、进度及计划，学生的学习要求、目标、计划及考试等教与学各方面的事务，是学校的主要机构之一。该机构的负责人为教务处长（或教务长，也有的叫教导主任）。',
          'partone': [{
            'name': '张1',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'parttwo': [{
            'name': '李四',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '王五',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }]
        }, {
          'partname': '人事处',
          'partfunc': '人事处，要严格保守党和国家机密。妥善保管机密文件、材料，不该说的不说，不该问的不问，通信和公共场所不谈机密问题。 ',
          'partone': [{
            'name': '张1',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'parttwo': [{
            'name': '李四',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '王五',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'partother': [{
            'name': '甲',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '乙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丁',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }]
        }, {
          'partname': '学员工作处',
          'partfunc': '学生工作处（简称学工处）是指在高校或省级教育部门中设置的主要负责学生事务的工作机构。在高校党委（教育厅党委）和行政（教育厅行政）的职能部门，根据教育行政部门和高校党委、行政关于学生工作的指导思想和原则，创造性地开展学校工作。本着统筹、协调、指导和服务的原则，负责高校学生的思想政治教育、行为规范管理、成长成才服务。',
          'partone': [{
            'name': '张1',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'parttwo': [{
            'name': '李四',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '王五',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '副部长',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }],
          'partother': [{
            'name': '甲',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '乙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丙',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }, {
            'name': '丁',
            'detail': {
              'phone': '13215575315',
              'email': '13123@qq.com',
              'name': '张1',
              'do': '科员',
              'sex': '男',
              'birth': '1980-9-1',
              'state': '本科',
              'sch': '嘉兴学院',
              'party': '党员',
              'time': '2014-9-3'
            }
          }]
        }]
      }
    },
    created(){
      document.body.style.backgroundColor = 'white'
      this.partname = this.partinfo[0].partname
      this.singleinfo = this.partinfo[0]
    },
    components: {
      headersome
    },
    methods: {
      edit(index){
        console.log(index)
        console.log(this.singleinfo)
        console.log(this.singleinfo.partone[0])
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon1')[index].style.color = 'red'
        this.singeldetail = this.singleinfo.partone[index].detail
        console.log(this.singleinfo)
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
      },
      edit2(index){
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon2')[index].style.color = 'red'
        this.singeldetail = this.singleinfo.parttwo[index].detail
        document.getElementsByClassName('partinfo-modal')[0].style.bottom = '0'
      },
      edit3(index){
        for (let i of document.getElementsByClassName('partinfoicon')) {
          i.style.color = 'black'
        }
        document.getElementsByClassName('partinfoicon3')[index].style.color = 'red'
        this.singeldetail = this.singleinfo.partone[index].detail
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
        this.partname = command
        for (let i of this.partinfo) {
          if (i.partname === command) {
            this.singleinfo = i
          }
        }
      }
    }
  }
</script>

<style lang="stylus" type="text/stylus">
  @import '../common/css/partinfo'
</style>
