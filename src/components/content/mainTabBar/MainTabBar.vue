<template>
  <tab-bar>
    <tab-bar-item path1="/home">
      <img slot="item-icon" src="~assets/img/tabbar/home.png"/>
      <img slot="item-icon-activated" src="~assets/img/tabbar/home_active.png"/>
      <div slot="item-text">首页</div>
    </tab-bar-item>

    <tab-bar-item path1="/category">
      <img slot="item-icon" src="~assets/img/tabbar/category.png"/>
      <img slot="item-icon-activated" src="~assets/img/tabbar/category_active.png"/>
      <div slot="item-text">分类</div>
    </tab-bar-item>

    <tab-bar-item path1="/cart">
      <img slot="item-icon" src="~assets/img/tabbar/shopcart.png"/>
      <img slot="item-icon-activated" src="~assets/img/tabbar/shopcart_active.png"/>
      <div slot="item-text">购物车</div>
    </tab-bar-item>

    <tab-bar-item path1="/profile">
      <img slot="item-icon" src="~assets/img/tabbar/profile.png"/>
      <img slot="item-icon-activated" src="~assets/img/tabbar/profile_active.png"/>
      <div slot="item-text">我的</div>
    </tab-bar-item>
  </tab-bar>
</template>
<script>
  import TabBar from 'components/common/tabbar/TabBar.vue'
  import TabBarItem from 'components/common/tabbar/TabBarItem.vue'

  export default {
    name: `MainTabBar`,
    components:{
      TabBar,
      TabBarItem,
    }
  }
</script>
<style scoped>

</style>
