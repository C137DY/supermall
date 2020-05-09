<template>
  <div class="wrapper" ref="wrapper">


  <ul class="content">
    <li>分类列表</li>
    <li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
    <li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li><li>分类列表</li>
  </ul>
  </div>
</template>
<script>
  import BSCroll from 'better-scroll'
  export default {
    name: 'Category',
    data(){
      return {
        scroll: null
      }
    },
    //组件挂载后使用
    mounted(){
      this.scroll = new BSCroll(this.$refs.wrapper,{
        //侦测  0、1 不侦测实时位置  2 在手指滚动过程中侦测，手指离开后的惯性不侦测  3 只要滚动就侦测
        probeType:  3,
        pullUpLoad: true
      })
      this.scroll.on('scroll',(position) => {
        console.log(position);
      })
      this.scroll.on('pullingUp',() => {
        console.log("上拉加载数据");
        //网络请求

        //等数据请求完成，并且将新的数据展示出来后
        setTimeout(() => {
          this.scroll.finishPullUp();
        },2000)
      })
    }
  }
</script>
<style scoped>
  .wrapper{
    height: 150px;
    background-color: red;

    /*overflow: hidden;*/
    /*overflow-y: scroll;*/
  }
</style>
