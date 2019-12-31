
<template>
  <div>
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>

    <h1>Vue Home</h1>

  </div>
</template>

<script>

  import NavBar from 'components/common/navbar/NavBar.vue'
  import {getHomeMultidata} from 'network/home';

  export default {
    name: 'Home',
    data() {
      return {
        result: null,
        banners: [],
        recommends: [],

      }
    },
    components: {
      NavBar
    },
    created() {  ////创建完成 

      getHomeMultidata().then(res => {
        console.log(res);
        this.result = res.data
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend


      })


    },

  }
</script>

<style scoped>
  .home-nav {
    background-color: crimson;
    color: #ffffff;
  }
</style>