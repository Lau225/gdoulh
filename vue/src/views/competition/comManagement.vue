<template>
<div>
  <div class="top">
    <div class="top_top">
      <div class="eventManager" v-show="roleId==4||roleId==1?true:false">
        <span class="top_text" @click="competitionReview"
              :class="$route.path=='/home/comManagement/competitionReview'?'active':''">赛事审核</span>
        <span class="top_text" @click="comFieldArrange"
              :class="$route.path=='/home/comManagement/comFieldArrange'?'active':''">比赛场地安排</span>
      </div>
    </div>
    <div class="top_bottom">
      <div class="teacher" v-show="roleId==7||roleId<6?true:false">
        <span class="top_text" @click="createCompetition"
              :class="$route.path=='/home/comManagement/competitionCreate'?'active':''">赛事创建(预告)</span>
        <span class="top_text" @click="competitionCancel"
              :class="$route.path=='/home/comManagement/competitionCancel'?'active':''">赛事取消</span>
        <span class="top_text" @click="comEquipArrange"
              :class="$route.path=='/home/comManagement/comEquipArrange'?'active':''">赛事器材安排</span>
        <span class="top_text" @click="refereeAnnouncement"
              :class="$route.path=='/home/comManagement/refereeAnnouncement'?'active':''">裁判简介公告</span>
      </div>
      <div class="user" v-show="roleId<8?true:false">
        <span class="top_text" @click="competitionQuery"
              :class="$route.path=='/home/comManagement/competitionQuery'?'active':''">赛事查询</span>
        <span class="top_text" @click="queryRefereeAnn"
              :class="$route.path=='/home/comManagement/queryRefereeAnn'?'active':''">查询裁判公告</span>
      </div>
    </div>
  </div>
  <router-view></router-view>
</div>
</template>

<script>
export default {
  data(){
    return{
      roleId:20,     // 角色权限id 
    }
  },
  created(){
    this.roleId = localStorage.getItem("roleId")
  },
  methods:{
    createCompetition(){
      this.$router.push({path:"/home/comManagement/competitionCreate"})
    },
    competitionReview(){
      this.$router.push({path:"/home/comManagement/competitionReview"})
    },
    competitionCancel(){
      this.$router.push({path:"/home/comManagement/competitionCancel"})
    },
    competitionQuery(){
      this.$router.push({path:"/home/comManagement/competitionQuery"})
    },
    comFieldArrange(){
      this.$router.push({path:"/home/comManagement/comFieldArrange"})
    },
    comEquipArrange(){
      this.$router.push({path:"/home/comManagement/comEquipArrange"})
    },
    comEquipReview(){
      this.$router.push({path:"/home/comManagement/comEquipReview"})
    },
    refereeAnnouncement(){
      this.$router.push({path:"/home/comManagement/refereeAnnouncement"})
    },
    queryRefereeAnn(){
      this.$router.push({path:"/home/comManagement/queryRefereeAnn"})
    }
  }
}
</script>

<style scoped lang="less">
.top{
  width:100%;
  .top_top,.top_bottom{
    display: flex;
    border-bottom: 1px solid #dcd8d8;
  }
  .top_text{
    cursor: pointer;
    margin-left: 40px;
    height: 40px;
    line-height: 40px;
    padding: 10px;
  }
  .active{
    color:deepskyblue;
    border-bottom: 1px solid deepskyblue;
  }
}
/deep/ *{
  overflow: hidden;
}
.el-tabs{
  i{
    margin-left: 7%;
  }
}
.el-tabs__item{
  height: 500px;
}
/deep/.el-tabs__nav-scroll {
  overflow: hidden;
  height: 45px;
  font-size: 18px;
  margin-left: 35%;
}
</style>