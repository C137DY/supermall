<template>
  <!--<div class="tab-bar-item">首页</div>-->
  <div class="tab-bar-item" @click="itemClick">

    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>

    <div v-else>
      <slot name="item-icon-activated"></slot>
    </div>

    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>

    <!--<img src="../assets/img/tabbar/ziyuan.svg"/>-->
    <!--<div>首页</div>-->

  </div>
  <!--<div class="tab-bar-item">-->
    <!--<img src="./assets/img/tabbar/appstore.svg"/><div>分类</div></div>-->
  <!--<div class="tab-bar-item">-->
    <!--<img src="./assets/img/tabbar/cart_icon.svg"/><div>购物车</div></div>-->
  <!--<div class="tab-bar-item">-->
    <!--<img src="./assets/img/tabbar/wode.svg"/><div>我的</div></div>-->
</template>
<script>
  export default {
    name: 'TabBarItem',
    props: {
      path1: String,
      activeColor: {
        type: String,
        default: '#e95d8d'
      },
    },
    data(){
      return {
//        isActive: true
      }
    },
    computed: {
      isActive(){
        return this.$route.path.indexOf(this.path1) !== -1
      },
      activeStyle(){
        return this.isActive ? {color: this.activeColor} : {}
      }
    },
    methods:{
      itemClick(){
        this.$router.replace(this.path1)
      }
    }
  }
</script>

<style scoped>
  .tab-bar-item{
    flex: 1;
    height: 49px;
    text-align: center;
  }
  .tab-bar-item img{
    width: 25px;
    height: 25px;
    margin-top: 3px;
    font-size: 14px;
    vertical-align: middle;
  }
  /*.active{*/
    /*color: red;*/
  /*}*/
</style>

