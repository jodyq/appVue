<!--src/componets/home/NewsList.vue-->
<template>
  <div class="app-newslist">
		<ul class="mui-table-view">
				<li class="mui-table-view-cell mui-media" v-for="item in list" :key="item.id">
					<router-link :to="'/NewsInfo?nid='+item.id">
						<img class="mui-media-object mui-pull-left" :src="item.img_url">
						<div class="mui-media-body">
							  {{item.title}}
							<p class='mui-ellipsis'>
              <span>{{item.ctime | datetimeFilter}}</span>
              <span>点击{{item.point}}次</span>
              </p>
						</div>
					</router-link>
				</li>
     </ul>
     <mt-button type="primary" size="large" @click="getMore">加载更多</mt-button>
  </div> 
</template>
<script>
  export default {
    data(){
       return {
         list:[],
         pno:1,
         pageSize:7
         }
    },
    methods:{
      getMore(){
          this.pno++;
          var url="http://127.0.0.1:3000";
          url+="/newslist?pno="+this.pno;
          url+="&pageSize="+this.pageSize;
          this.axios.get(url).then(result=>{
            var rows=this.list.concat
            (result.data.data);
            this.list = rows;
        })
      },
     //mui查找 左面图片右面文字
     getnewsList(){
      var url = "http://127.0.0.1:3000/newslist";
      this.axios.get(url).then(result=>{
         this.list = result.data.data;
      })
     }
    },
    created() {
      this.getnewsList();
    },
  }  
</script>
<style>
  /*日期和点击次数两端对齐*/
  .app-newslist li .mui-ellipsis{
    display:flex;   /*弹性布局*/
    font-size:12px;
    color:#226aff;
    justify-content:space-between;/*两端对齐*/
  }
</style>