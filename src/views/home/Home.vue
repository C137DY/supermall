<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <scroll class="content" ref="content">
      <!-- 滚动条 -->
      <home-swiper :banners="banners"></home-swiper>
      <!-- 推荐内容 -->
      <recommend-view :recommends="recommends"></recommend-view>
      <!-- 本周流行 -->
      <feature-view/>
      <!-- 商品选择栏 -->
      <tab-control class="tab-control" :titles="['新款','流行','精选']" @changeItem="changeItem"></tab-control>
      <!-- 商品列表 -->
      <goods-list :goods="goods[this.currentType].list"></goods-list>
    </scroll>
    <back-top @click.native="backClick"></back-top>
  </div>
</template>
<script>
  import NavBar from 'components/common/navbar/NavBar'
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView.vue'
  import TabControl from 'components/content/tabControl/TabControl'
  import GoodsList from 'components/content/goods/GoodsList'
  import Scroll from "components/common/scroll/Scroll";
  import BackTop from "components/content/backtop/BackTop"

  import {getHomeMultidata,getHomeGoods} from 'network/home'

  export default {
    name: 'Home',
    components: {
      FeatureView,
      NavBar,
      HomeSwiper,
      RecommendView,
      TabControl,
      GoodsList,
      Scroll,
      BackTop
    },
    data(){
      return {
        currentType: 'pop',
        banners: [],
        recommends: [],
        goods: {
          'pop': {page: 0,list: []},
          'new': {page: 0,list: []},
          'sell': {page: 0,list: []}
        }
      }
    },
    methods: {
      backClick(){
        this.$refs.content.scrollTo(0,0)
      },
      changeItem(index){
        switch (index) {
          case 0:
            this.currentType = 'pop'
            break
          case 1:
            this.currentType = 'new'
            break
          case 2:
            this.currentType = 'sell'
            break
        }
      },
      getHomeMultidata(){
        //1 获取请求数据
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
          console.log(this.banners);
        })
      },
      getHomeGoods(type) {
        const page = this.goods[type].page + 1
        getHomeGoods(type, page).then(res => {
          console.log(res);
          this.goods[type].list.push(...res.data.list)
          this.goods[type].page += 1
        })
      }
    },
    //vue生命周期，组件创建前调用
    created(){
      this.getHomeMultidata();

      // 2.请求商品数据
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')
      //1 获取请求数据
//      getHomeMultidata().then(res => {
//        this.banners = res.data.banner.list;
//        this.recommends = res.data.recommend.list;
//        console.log(this.banners);
//      })
//
//      getHomeGoods('pop',1).then(res => {
//        console.log(res);
//      })
    }
  }
</script>

<style scoped>
  #home{
    height: 100vh;
    position: relative;

  }
 .home-nav{
   background-color: var(--color-tint);
   color: #fff;

   position: fixed;
   left: 0;
   right: 0;
   top: 0;
   z-index: 9;
 }
  .tab-control{
    /*position: sticky;*/
    top: 44px;
    z-index: 9;
  }
  .content{
    /*overflow: hidden;*/
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0px;
    right:0px;
  }
</style>

