<template>
  <div class="app-memberInfo">
      <ul class="mui-table-view mui-table-view-striped mui-table-view-condensed">
				<li class="mui-table-view-cell">
					<div class="mui-slider-cell">
						<div class="oa-contact-cell mui-table">
							<div class="oa-contact-avatar mui-table-cell">
								<img src="img/60x60.gif" />
							</div>
							<div class="oa-contact-content mui-table-cell">
								<div class="mui-clearfix">
									<h4 class="oa-contact-name">Tom</h4>
									<span class="oa-contact-position mui-h6">商城会员</span>
								</div>
								<p class="oa-contact-email mui-h6">
									123e@126.com
								</p>
							</div>
						</div>
					</div>
				</li>
      </ul>

      <ul class="mui-table-view">
				<li class="mui-table-view-cell">
					<a class="mui-navigate-right">
						我的收货地址
					</a>
				</li>
				<li class="mui-table-view-cell">
					<a class="mui-navigate-right">
						隐私
					</a>
				</li>
				<li class="mui-table-view-cell">
					<a class="mui-navigate-right">
						通用
					</a>
				</li>
			</ul>
			<ul class="mui-table-view" style="margin-top: 25px;">
				<li class="mui-table-view-cell">
					<a class="mui-navigate-right">
						关于商城应用
					</a>
				</li>
			</ul>
			<ul class="mui-table-view" style="margin-top: 25px;">
				<li class="mui-table-view-cell">
					<a style="text-align: center;color: #FF3B30;" @click="logOut">
						退出登录
					</a>
				</li>
			</ul>
    </div>
</template>
<script>
  import {Toast} from "mint-ui"
  export default {
     data(){
       return {}
     },
     created() {
       
     },
      methods:{
      logOut(){ 
         var url = "http://127.0.0.1:3000/logout";
       this.axios.get(url).then(res=>{
            Toast("己退出");
       })
        this.$router.push('/Login')          	      
      },
  }
  }
</script>
<style>
</style>
