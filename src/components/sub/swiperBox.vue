<!--  \src\components\sub\comment.vue -->
<!-- src/componets/goods/GoodInfo.vue-->
<template>
  <!-- 外层父元素-->
  <div class="app-swiper">
    <!--轮播图-->
    <mt-swipe :auto="3000">
      <mt-swipe-item v-for="item in list" :key="item.id">
          <img :src="item.img_url" />
      </mt-swipe-item>
    </mt-swipe>
  </div>
</template>
<script>
  export default {
    data(){
      return{}
    },
    props:["list"],//接收父组件数据
    created() {
     
    },
    methods:{
      getMore(){
        this.pno++;
        var url = "http://127.0.0.1:3000";
        url+="/products?pno="+this.pno
        url+="&pageSize="+this.pageSize;
        this.axios.get(url).then(result=>{
          var rows = this.list.concat(result.data.data);
          this.list = rows;
        })
      }
    }
  }
</script>
<style>
   /*轮播图*/
 .app-swiper .mint-swipe{
   height:200px;
 }
 .app-swiper .mint-swipe img{
   width:100%;
 }
</style>
