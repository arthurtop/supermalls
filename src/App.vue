<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <main-tab-bar></main-tab-bar>


  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
  import MainTabBar from 'content/mainTabbar/MainTabBar'

export default {
  name: 'app',
  components: {
    // HelloWorld
    MainTabBar
  }
}
</script>

<style>

/* @import '@assets/css/base.css' */


</style>
