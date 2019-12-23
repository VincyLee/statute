/*
 * @Author: lk 
 * @Date: 2018-09-21 14:54:24 
 * @Last Modified by: lk
 * @Last Modified time: 2019-12-23 15:48:59
 * @Description:  
 */
<template>
  <div :class="{navbar:true,'no-text-select':true,'currentColor':$route.name!=='home'}" >
    <div class="base-container clearfix">
      <div class="logo">
        <a href="javascript:;" >军地政策法规智能辅助系统</a>
      </div>
      <ul class="left-menu clearfix">
        <li :class="{actived:$route.name==='home'}">
          <router-link to="/">首页</router-link>
        </li>
        <li :class="{actived:$route.name==='statistics'}">
          <router-link to="statistics">数据统计</router-link>
        </li>
        <li :class="{actived:$route.name==='analysis'}">
          <router-link to="analysis">模型分析</router-link>
        </li>
        <li :class="{actived:$route.name==='learn'}">
          <router-link to="learn">学习路上</router-link>
        </li>
      </ul>
      <ul class="right-menu clearfix">
          <li class="right-menu-item">
            <span class="log-out"> 
              <i class="log-user" :style="{backgroundImage:'url('+cutter+')'}"></i>
              <a  @click="logout">退出</a>
            </span>
          </li>
      </ul>
    </div>
  </div>
</template>

<script>
import cutter from '@/assets/images/cutter.png'
export default {
  data() {
    return {
      cutter
    }
  },
  computed: {
  },
  components: {
  },
  methods: {
    logout() {
      this.$confirm('确定注销当前登录吗?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        this.$store.dispatch('LogOut').then(() => {
          location.reload()
        })
      })
    }
  }
}
</script>
<style lang="scss" scoped>
.navbar {
  height: 60px;
  line-height: 60px;
  &.currentColor{
    background-color: $mainColor;
  }
  .logo{
    float: left;
    font-size: 20px;
    font-weight: bold;
    color: #fff;
    letter-spacing: 2px;
  }
  .left-menu{
    float: left;
    margin-left:60px;
    margin-top:18px;
    li{
      margin-left:10px;
      height: 27px;
      line-height:24px;
      &.actived{
        border-bottom: 2px solid #fff;
      }
      a{
        color:#fff;
        font-size: 14px;
        padding:0 5px;
        height: 24px;
      }
    }
  }
  .right-menu{
    float: right;
    .right-menu-item{
      float: left;
      .log-out{
        font-size: 14px;
        color:#fff;
        position: relative;
        .log-user{
          position: absolute;
          top:-4px;
          left: -40px;
          width: 26px;
          height: 26px;
          background-position: 55px 210px;
        }
      }
    }
  }
  .left-menu,.right-menu{
    list-style: none;
    li{
      float:left;
    }
  }
}
</style>
