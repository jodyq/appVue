<template>
  <div class="app-login">
     <!--登录页面-->
		 <header class="mui-bar mui-bar-nav">
			<h1 class="mui-title">登录</h1>
		</header>
		
			<div class="mui-card">
				<div class="mui-card-content">
					<div class="mui-card-content-inner">
						<div class="mui-content">
							<form  class="mui-input-group">
								<div class="mui-input-row" style="height:55px;">
									<label>账号</label>
									<input v-model="uname" type="text" class="mui-input-clear mui-input" placeholder="请输入账号">
								</div>
								<div class="mui-input-row" style="height:55px;">
									<label>密码</label>
									<input v-model="upwd" type="password" class="mui-input-clear mui-input-password" placeholder="请输入密码">
								</div>
								<input id='login' type="button" class="mui-btn mui-btn-block mui-btn-primary" 
								style="height:40px;background:#26a2ff;border-radius:4px;color:#fff;" @click="login" value="登录"/>
							</form>
							<!-- <form class="mui-input-group">
								<ul class="mui-table-view mui-table-view-chevron">
									<li class="mui-table-view-cell">
										自动登录
										<div id="autoLogin" class="mui-switch">
											<div class="mui-switch-handle"></div>
										</div>
									</li>
								</ul>
							</form>
							<div class="mui-content-padded">
								<button id='login' type="button" class="mui-btn mui-btn-block mui-btn-primary" @click="login">登录</button>
								<div class="link-area"><a id='reg'>注册账号</a> <span class="spliter">|</span> <a id='forgetPassword'>忘记密码</a>
								</div>
							</div>
							<div class="mui-content-padded oauth-area">

							</div> -->
							<div class="mui-content-padded oauth-area">		
						</div>
					</div>
				</div>
			</div>
			</div>
			
  </div>
</template>
<script>
import {Toast} from "mint-ui";
  export default {
    data(){
      return {
          uname:"",
					upwd:""
      }
    },
    created() {
		//  var tab = document.getElementById("tabBar");
		//  console.log(tab);
    },
    methods:{
      login(){ 
				var n=this.uname;
				var p=this.upwd;
			 	var reg= /^[a-z0-9]{3,12}$/i;
			 	if(!reg.test(n))
				{
			 		Toast("用户名格式不正确！");
					return;
			 	}
       //2:发送ajax 请求
       var url = "http://127.0.0.1:3000/";
			 url+="login?uname="+n+"&upwd="+p;
       this.axios.get(url).then(result=>{
					if(result.data.code==1)
					{
							//Toast("登录成功！");
							 this.$router.push("/Home")
					}else{
							Toast("用户名或密码有误！");
					}
       });
       //3:获取返回数据 显示  
      }
    }
  }//default end 
</script>
<style>
</style>