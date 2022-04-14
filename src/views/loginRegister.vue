<template>
	<div class="login-register">
		<div class="contain">
			<div class="big-box" :class="{active:isLogin}">


				<div class="big-contain" v-if="isLogin">
					<div class="btitle">账户登录</div>
					<div class="bform">

						<input type="userName" placeholder="用户名" v-model="form.userName">
						<span class="errTips" v-if="emailError">* 用户名写错误 *</span>
						<input type="password" placeholder="密码" v-model="form.userpwd">
						<span class="errTips" v-if="emailError">* 密码填写错误 *</span>
					</div>


					<button class="bbutton" @click="login">登录</button>


					<p><br></p>


					<button class="bbutton" @click="changeType">忘记密码</button>

				</div>


				<div class="big-contain" v-else>
					<div class="btitle">创建账户</div>
					<div class="bform">
						<input type="text" placeholder="用户名" v-model="form.userName">
						<span class="errTips" v-if="existed">* 用户名已经存在！ *</span>

						<input type="text" placeholder="昵称" v-model="form.nickName">
						<input type="password" placeholder="密码" v-model="form.userpwd">
					</div>
					<button class="bbutton" @click="register">注册</button>
				</div>

			</div>





			<div class="small-box" :class="{active:isLogin}">


				<div class="small-contain" v-if="isLogin">
					<div class="stitle">你好，朋友!</div>
					<p class="scontent">开始注册，和我们一起旅行</p>
					<button class="sbutton" @click="changeType">注册</button>



				</div>






				<div class="small-contain" v-else>
					<div class="stitle">欢迎回来!</div>
					<p class="scontent">与我们保持联系，请登录你的账户</p>
					<button class="sbutton" @click="changeType">登录</button>

					


				</div>




			</div>
		</div>
		<p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p>



		<div class="contain">
			<div class="big-box" :class="{active:isLogin}">

				<div class="big-contain" v-if="isLogin">
					<div class="btitle">修改密码</div>
					<div class="bform">

						<input type="password" placeholder="新密码" v-model="form.userpwd">

						<input type="password" placeholder="确认密码" v-model="form.userpwd">
					</div>
					<button class="bbutton" @click="login">确认修改</button>
				</div>


				<div class="big-contain" v-else>
					<div class="btitle">验证信息</div>
					<div class="bform">
						<input type="text" placeholder="用户名" v-model="form.userName">
						<input type="text" placeholder="真实姓名" v-model="form.realName">
						<input type="text" placeholder="联系方式" v-model="form.Contactinfor">
					</div>
					<button class="bbutton" @click="register">注册</button>
				</div>

			</div>


			<div class="small-box" :class="{active:isLogin}">
				<div class="small-contain" v-if="isLogin">
					<div class="stitle">第二步</div>
					<p class="scontent"><br></p>
					<button class="sbutton" @click="changeType">上一步</button>
				</div>


				<div class="small-contain" v-else>
					<div class="stitle">第一步</div>
					<p class="scontent">请先完成第一步</p>
					<button class="sbutton" @click="changeType">下一步</button>
				</div>
			</div>
		</div>





		
		<p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p>




		<p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p>



		<div class="contain">
			<div class="big-box" :class="{active:isLogin}">

				<div class="big-contain" v-if="isLogin">
					<div class="btitle">修改密码</div>
					<div class="bform">

						<input type="password" placeholder="新密码" v-model="form.userpwd">

						<input type="password" placeholder="确认密码" v-model="form.userpwd">
					</div>
					<button class="bbutton" @click="login">确认修改</button>
				</div>


				<div class="big-contain" v-else>
					<div class="btitle">验证</div>
					<div class="bform">
						<input type="password" placeholder="原密码" v-model="form.userpwd">
					</div>
					<button class="bbutton" @click="register">验证</button>
				</div>

			</div>


			<div class="small-box" :class="{active:isLogin}">
				<div class="small-contain" v-if="isLogin">
					<div class="stitle">第二步</div>
					<p class="scontent"><br></p>
					<button class="sbutton" @click="changeType">上一步</button>
				</div>


				<div class="small-contain" v-else>
					<div class="stitle">第一步</div>
					<p class="scontent">请先完成第一步</p>
					<button class="sbutton" @click="changeType">下一步</button>
				</div>
			</div>
		</div>





		
		<p><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br></p>




	</div>






	
</template>

<script>
	export default{
		name:'login-register',


		data(){
			return {
				isLogin:false,

				emailError: false,
				passwordError: false,
				existed: false,

				nickName: false,
				userName: false,
				changepassword: false,

				form:{
					userName:'',
					useremail:'',
					userpwd:'',

					nickName:'',
					realName:'',
					Contactinfor:''
				}
			}
		},



		methods:{



			changeType() {
				this.isLogin = !this.isLogin
				

				this.form.userName = ''

				this.form.useremail = ''

				this.form.userpwd = ''



				this.form.nickName = ''
				this.form.realName = ''
				this.form.Contactinfor = ''
				
				this.form.changepassword = !this.changepassword


			},




			login() {
				const self = this;
				if (self.form.userName != "" && self.form.userpwd != "") {
					self.$axios({
						method:'post',
						url: '替换接口',
						data: {
							userName: self.form.userName,
							password: self.form.userpwd
						}
					})


					.then( res => {
						switch(res.data){
							case 0: 
								alert("登陆成功！");
								break;
							case -1:
								this.userNameError = true;
								break;
							case 1:
								this.passwordError = true;
								break;
						}
					})
					.catch( err => {
						console.log(err);
					})
				} else{
					alert("填写不能为空！");
				}
			},








			register(){
				const self = this;
				if(self.form.username != "" && self.form.nickName != "" && self.form.userpwd != ""){
					self.$axios({
						method:'post',
						url: '替换接口',
						data: {
							username: self.form.username,
							nickName: self.form.nickName,
							password: self.form.userpwd
						}
					})
					.then( res => {
						switch(res.data){
							case 0:
								alert("注册成功！");
								this.login();
								break;
							case -1:
								this.existed = true;
								break;
						}
					})
					.catch( err => {
						console.log(err);
					})
				} else {
					alert("填写不能为空！");
				}
			},



			forgetpassword(){
				const self = this;
				if (self.form.userName != "" && self.form.userpwd != "") {
					self.$axios({
						method:'post',
						url: '替换接口',
						data: {
							userName: self.form.userName,
							password: self.form.userpwd
						}
					})


					.then( res => {
						switch(res.data){
							case 0: 
								alert("登陆成功！");
								break;
							case -1:
								this.userNameError = true;
								break;
							case 1:
								this.passwordError = true;
								break;
						}
					})
					.catch( err => {
						console.log(err);
					})
				} else{
					alert("填写不能为空！");
				}
			},



			checkpassword(){

			},


			changepassword(){

			}







		}
	}
</script>

<style scoped="scoped">
	.login-register{
		width: 100vw;
		height: 100vh;
		box-sizing: border-box;
	}
	.contain{
		width: 60%;
		height: 60%;
		position: relative;
		top: 50%;
		left: 50%;
		transform: translate(-50%,-50%);
		background-color: #fff;
		border-radius: 20px;
		box-shadow: 0 0 3px #f0f0f0,
					0 0 6px #f0f0f0;
	}
	.big-box{
		width: 70%;
		height: 100%;
		position: absolute;
		top: 0;
		left: 30%;
		transform: translateX(0%);
		transition: all 1s;
	}
	.big-contain{
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.btitle{
		font-size: 1.5em;
		font-weight: bold;
		color: rgb(57,167,176);
	}
	.bform{
		width: 100%;
		height: 40%;
		padding: 2em 0;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
	}
	.bform .errTips{
		display: block;
		width: 50%;
		text-align: left;
		color: red;
		font-size: 0.7em;
		margin-left: 1em;
	}
	.bform input{
		width: 50%;
		height: 30px;
		border: none;
		outline: none;
		border-radius: 10px;
		padding-left: 2em;
		background-color: #f0f0f0;
	}
	.bbutton{
		width: 20%;
		height: 40px;
		border-radius: 24px;
		border: none;
		outline: none;
		background-color: rgb(57,167,176);
		color: #fff;
		font-size: 0.9em;
		cursor: pointer;
	}
	.small-box{
		width: 30%;
		height: 100%;
		background: linear-gradient(135deg,rgb(57,167,176),rgb(56,183,145));
		position: absolute;
		top: 0;
		left: 0;
		transform: translateX(0%);
		transition: all 1s;
		border-top-left-radius: inherit;
		border-bottom-left-radius: inherit;
	}
	.small-contain{
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.stitle{
		font-size: 1.5em;
		font-weight: bold;
		color: #fff;
	}
	.scontent{
		font-size: 0.8em;
		color: #fff;
		text-align: center;
		padding: 2em 4em;
		line-height: 1.7em;
	}
	.sbutton{
		width: 60%;
		height: 40px;
		border-radius: 24px;
		border: 1px solid #fff;
		outline: none;
		background-color: transparent;
		color: #fff;
		font-size: 0.9em;
		cursor: pointer;
	}
	
	.big-box.active{
		left: 0;
		transition: all 0.5s;
	}
	.small-box.active{
		left: 100%;
		border-top-left-radius: 0;
		border-bottom-left-radius: 0;
		border-top-right-radius: inherit;
		border-bottom-right-radius: inherit;
		transform: translateX(-100%);
		transition: all 1s;
	}
</style>
