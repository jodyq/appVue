<template>
  <div class="app-home">
   <!--顶部导航条 -->
   <!--轮播图-->
   <mt-swipe>
     <mt-swipe-item v-for="item in list" :key="item.id">
         <img :src="item.img_url" />
     </mt-swipe-item>
   </mt-swipe>
   <!--九宫格 -->
    <ul class="mui-table-view mui-grid-view mui-grid-9">   
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
            <router-link to="/GoodsList">
              <a href="#">
              <img src="../../img/menu2.png" />
              <div class="mui-media-body">商品</div></a>
            </router-link> 
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
          <router-link to="/ShopCart">
            <a href="#">
              <img src="../../img/menu3.png" />
              <div class="mui-media-body">购物车</div></a>
            </router-link> 
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
          <router-link to="/NewsList">
              <a href="#"> 
              <img src="../../img/menu1.png" />
              <div class="mui-media-body">新闻咨讯</div></a>
            </router-link> 
        </li>
      
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
            <img src="../../img/menu4.png" />
            <div class="mui-media-body">支付</div></a>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3">
            <a href="#">
            <img src="../../img/menu5.png" />
            <div class="mui-media-body">搜索</div></a>
        </li>   
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-3"><a href="#">
            <img src="../../img/menu6.png" />
            <div class="mui-media-body">更多</div></a>
        </li>    
    </ul>    
<!--tabbar -->
  </div>
</template>
<script>
  export default {
     data(){
       return {
         list:[
          //  {id:1,img_url:"img/banner1.png"},//访问public路径下的img公共文件夹的方式
          //  {id:2,img_url:"img/banner2.png"},
          //  {id:3,img_url:"img/banner3.png"},
         ]
       }
     },
     //这里是通过请求后台数据的方法获取图片
     methods:{
         handleImage(){
        //1:发送ajax请求给服务器
        var url = "http://127.0.0.1:3000/imageList";
           this.axios.get(url).then(result=>{
               //console.log(result.data);
               this.list = result.data;
           });
           //2:接收服务器返回结果
           //3:将结果保存list
         }
     },
     created() {
        this.handleImage(); 
     },
  }
</script>
<style>
  /*轮播图*/
 .app-home .mint-swipe{
   height:200px;
 }
 .app-home .mint-swipe img{
   width:100%;
 }
 /*九宫格  图片宽度*/
 .app-home .mui-grid-9 img{
    width:60px;
    height:60px;	 
 }
  /*九宫格  背景修改为白色*/
 .app-home .mui-grid-view.mui-grid-9{
    background-color:#fff; 
 }

</style>