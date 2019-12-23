<template>
  <div class="app-wrapper" >
    <navbar></navbar>
    <div class="main-container">
      <app-main ></app-main>
    </div>
  </div>
</template>

<script>
import { Navbar, AppMain } from './components'

export default {
  name: 'layout',
  components: {
    Navbar,
    AppMain
  },
  computed: {
  },
  created() {
    this.setCurrentHeight()
    this.$i18n.locale = this.$store.state.app.language
    window.addEventListener('resize', function() {
      this.setCurrentHeight()
    }.bind(this), false)
  },
  data() {
    return {
      height: null
    }
  },
  methods: {
    setCurrentHeight() {
      const height = document.body.offsetHeight - 96
      const dialogHeight = document.body.offsetHeight * 0.75
      const appWidth = document.body.offsetWidth - 210
      this.height = height + 'px'
      this.$store.dispatch('setContainHeight', { height, dialogHeight, appWidth })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  .app-wrapper {
   // @include clearfix;
    position: relative;
    height: 100%;
    width: 100%;
    overflow: hidden;
  }
  .drawer-bg {
    background: #000;
    opacity: 0.3;
    width: 100%;
    top: 0;
    height: 100%;
    position: absolute;
    z-index: 999;
  }
</style>
