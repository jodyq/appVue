<template>
 <div class="app-container">
     <!--顶部导航条 -->
    <mt-header fixed title="商城应用"></mt-header>
    <router-view></router-view>
    <!--tabbar -->   
    <nav class="mui-bar mui-bar-tab" id="tabBar">     
        <a class="mui-tab-item mui-active" @click="jumpPage1" id="home">
            <span class="mui-icon mui-icon-home"></span>
            <span class="mui-tab-label">首页</span>
        </a> 
        <a class="mui-tab-item"  @click="jumpPage2" id="search">
            <span class="mui-icon mui-icon mui-icon-chatboxes"></span>
            <span class="mui-tab-label">消息</span>
        </a>        
        <a class="mui-tab-item" @click="jumpPage3" id="shopCart">
            <span class="mui-icon mui-icon-extra mui-icon-extra-cart">
            <span class="mui-badge">0</span>
            </span>
            <span class="mui-tab-label">购物车</span>
        </a>
         <a class="mui-tab-item"  @click="jumpPage4" id="memberInfo">
            <span class="mui-icon mui-icon-contact">
            </span>
            <span class="mui-tab-label">会员</span>
        </a>       
    </nav>
 </div>
</template>
<script>
  export default {
    data(){
      return {
         
      }
    },
    created() {
     
    },
    methods:{
      jumpPage1(){ 
         //切换选项卡高亮  
        var current = document.querySelector(".mui-bar-tab>.mui-tab-item.mui-active");  
        var defaultTab = document.getElementById("home");
        if (defaultTab !== current) {  
              current.classList.remove('mui-active');  
              defaultTab.classList.add('mui-active');  
        }
        this.$router.push('/home')          	      
      },
      jumpPage2(){ 
        //切换选项卡高亮  
        var current = document.querySelector(".mui-bar-tab>.mui-tab-item.mui-active");   
        var defaultTab = document.getElementById("search");       
        if (defaultTab !== current) {  
              current.classList.remove('mui-active');  
              defaultTab.classList.add('mui-active');  
        };
        this.$router.push('/NewsList');  
      },
      jumpPage3(){ 
         var current = document.querySelector(".mui-bar-tab>.mui-tab-item.mui-active");          
        var defaultTab = document.getElementById("shopCart");
        if (defaultTab !== current) {  
              current.classList.remove('mui-active');  
              defaultTab.classList.add('mui-active');  
      }
        this.$router.push('/shopCart')           
     },		
     jumpPage4(){ 
         var current = document.querySelector(".mui-bar-tab>.mui-tab-item.mui-active");   
        var defaultTab = document.getElementById("memberInfo");
        if (defaultTab !== current) {  
              current.classList.remove('mui-active');  
              defaultTab.classList.add('mui-active');  
      }
        // this.$options.methods.com(idx); 调用函数
        this.$router.push('/memberInfo') 	  
      },

    }
  }//default end 
</script>
<style>
   .app-container{
     padding-top:40px;
     padding-bottom:50px;
     overflow-x:hidden;
   }

 .mui-bar-tab .mui-tab-item-tao.mui-active {
    color: #007aff;
 }
.mui-bar-tab .mui-tab-item-tao {
    display: table-cell;
    overflow: hidden;
    width: 1%;
    height: 50px;
    text-align: center;
    vertical-align: middle;
    white-space: nowrap;
    text-overflow: ellipsis;
    color: #929292;
}
.mui-bar-tab .mui-tab-item-tao .mui-icon {
    top: 3px;
    width: 24px;
    height: 24px;
    padding-top: 0;
    padding-bottom: 0;
}

.mui-bar-tab .mui-tab-item-tao .mui-icon~.mui-tab-label {
   font-size:11px;
   display:block;
   overflow:hidden;
   text-overflow:ellipsis;

}
</style>
