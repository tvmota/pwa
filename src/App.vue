<template>
  <div class="app" id="app">
    <Banner />
    <Header />
    <Menu />

    <div class="main">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import Menu from './components/Menu'
import Banner from './components/Banner'

export default {
  components: { Header, Menu, Banner },
  created: function () {
    window.addEventListener('resize',this.windowResize);
  },
  destroyed: function () {
    window.removeEventListener('resize', this.windowResize);
  },
  methods: {
    windowResize () {
      let sizes = {
        h: window.innerHeight,
        w: window.innerWidth,
      }

      this.$store.dispatch('resizeWindow', sizes).then(() => false);
    },
  }
}
</script>

<style lang="scss">
  @import './assets/css/app.scss';
</style>
