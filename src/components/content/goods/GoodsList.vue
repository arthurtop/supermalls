/* eslint-disable vue/no-unused-components */
<template>
  <div class="goods">
    
    <goods-list-item v-for="(item,index) in goods" :goods-item="item" :key="index">

    </goods-list-item>

    {{goods}}
  </div>  
</template>

<script>

import GoodsListItems from './GoodsListItems';


export default {
  name: 'GoodsList',
  props: {
    goods: {
      type: Array,
      default() {
        return []
      }
    }
  },
  components: {
    // eslint-disable-next-line vue/no-unused-components
    GoodsListItems,
  }
}
</script>

<style>

</style>