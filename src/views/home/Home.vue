/* eslint-disable vue/valid-v-bind */
<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>

    <home-swiper :banners="banners"></home-swiper>
     
    <recommend-view :recommends="recommends"></recommend-view>

    <feature-view></feature-view>

    <tab-control :titles="['流行','新款','精选']" class="tab-control" @tabclick="tabClick"></tab-control>

    <goods-list :goods="goods"></goods-list>

    <h1>Vue Home</h1>
    
    <ul>
      <li>zhanhang1</li>
      <li>zhanhang2</li>
      <li>zhanhang3</li>
      <li>zhanhang4</li>
      <li>zhanhang5</li>
      <li>zhanhang6</li>
      <li>zhanhang7</li>
      <li>zhanhang8</li>
      <li>zhanhang9</li>
      <li>zhanhang10</li>
      <li>zhanhang11</li>
      <li>zhanhang12</li>
      <li>zhanhang13</li>
      <li>zhanhang14</li>
      <li>zhanhang15</li>
      <li>zhanhang16</li>
      <li>zhanhang17</li>
      <li>zhanhang18</li>
      <li>zhanhang19</li>
    </ul>
    <ul>
      <li>zhanhang1</li>
      <li>zhanhang2</li>
      <li>zhanhang3</li>
      <li>zhanhang4</li>
      <li>zhanhang5</li>
      <li>zhanhang6</li>
      <li>zhanhang7</li>
      <li>zhanhang8</li>
      <li>zhanhang9</li>
      <li>zhanhang10</li>
      <li>zhanhang11</li>
      <li>zhanhang12</li>
      <li>zhanhang13</li>
      <li>zhanhang14</li>
      <li>zhanhang15</li>
      <li>zhanhang16</li>
      <li>zhanhang17</li>
      <li>zhanhang18</li>
      <li>zhanhang19</li>
    </ul>

  </div>
</template>

<script>

  import NavBar from 'components/common/navbar/NavBar.vue';
  import TabControl from 'components/content/tabControl/TabControl.vue'
  // eslint-disable-next-line no-unused-vars
  import GoodsList from 'components/content/goods/GoodsList.vue'

  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'




  // eslint-disable-next-line no-unused-vars
  import {getHomeMultidata, getHomeGoods} from 'network/home';

 


  export default {
    name: 'Home',
    data() {
      return {
        result: null,
        banners: [],
        recommends: [],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []},
        }
      }
    },
    components: {
      NavBar,
      HomeSwiper,
      // eslint-disable-next-line vue/no-unused-components
      RecommendView,
      // eslint-disable-next-line vue/no-unused-components
      FeatureView,
      // eslint-disable-next-line vue/no-unused-components
      TabControl,
      GoodsList
    },
    created() {  ////创建完成 

      /// 获取头部信息
      this.getHomeMultidata()

      /// 获取列表数据 
      // eslint-disable-next-line no-unused-vars
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')

    },
    methods: {

      /// 事件监听 ///
      onclick() {
        console.log('tabClick');
      },


      /// 网络请求 ///
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          console.log(res);
          this.result = res.data
          this.banners = res.data.banner.list
          this.recommends = res.data.recommend.list

        })
      },
      
      getHomeGoods(type) {
        const page = this.goods[type].page + 1

        getHomeGoods(type, page).then(res => {
          console.log(res)
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page++
        })
      }


    }

  }
</script>

<style scoped>
  #home {
    padding-top: 44px;
  }

  .home-nav {
    background-color: crimson;
    color: #ffffff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;

  }

  .tab-control {
    position: sticky;  /* sticky 悬浮 */
    top: 44px;
  }
</style>