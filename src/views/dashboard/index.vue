/*
 * @Author: lk 
 * @Date: 2019-12-23 11:16:27 
 * @Last Modified by: lk
 * @Last Modified time: 2019-12-23 15:50:11
 * @Description:  首页
 */
<template>
  <div class="dashboard-container" :style="{backgroundImage:'url('+bj+')'}">
    <navbar></navbar>
  </div>
</template>
<script>
import bj from '@/assets/images/bj.jpg'
import Navbar from '../layout/components/Navbar'
export default {
  name: 'home',
  components: {
    Navbar
  },
  data() {
    return {
      bj
    }
  }
}
</script>

<style lang="scss" scoped>
  .dashboard-container{
    height: 100%;
    background-repeat: no-repeat;
    background-size: cover;
  }
</style>

