<template>
	<div class="login-bar tx-center">
		<router-link to="/">
			<img src="https://pic4.zhimg.com/80/v2-a47051e92cf74930bedd7469978e6c08_hd.png" class="logo" />
		</router-link>
		<div class="login-box">
			<span class="login" @click="change(1)">登录</span>
			<span class="sign"  @click="change(2)">注册</span>
			<form class="login-form" v-if="id==1">
				手机:<input type="text" id="mobile" />
				验证码:<input type="password" />
				<input type="button" class="btn btn-lg dark-fill" value="登录" @click="signUp()" />
			</form>
			<form class="login-form" v-if="id==2">
				用户:<input type="text" id="mobile" />
				密码:<input type="password" />
				<input type="button" class="btn btn-lg dark-fill" value="注册" @click="signUp()" />
			</form>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'login',
		data() {
			return {
				id:1,
				count:1
			};
		},
		created() {
			
		},
		methods: {
			change(count) {
				if(count==1){
					this.id=1
				}
				else
				this.id=2
			}
		}
	};
</script>

<style lang="scss" scoped>
	.login-bar {
		background-color: rgb(184, 229, 248);
		background-image: url("https://static.zhihu.com/heifetz/assets/sign_bg.db29b0fb.png");
		background-repeat: no-repeat;
		background-size: cover;
		width: 100%;
		height: 100vh;
		overflow: auto;
	}

	.logo {
		height: 74px;
		width: 116px;
		margin-bottom: 24px;
		margin-top: 100px;
	}

	.login-box {
		width: 380px;
		height: 300px;
		background-color: rgb(255, 255, 255);
		position: absolute;
		top: 200px;
		left: 40%;
	}

	.login {
		display: flex;
		position: absolute;
		top: 10px;
		left: 10px;
	}
	.sign{
		position: absolute;
		top: 10px;
		left: 50px;
	}

	.login-form {
		padding-top: 50px;
		width: 70%;
		margin: 0 auto;
		text-align: left;
	}

	.login-form input {
		width: 100%;
		height: 25px;
		outline: none;
		border: none;
		margin-bottom: 20px;
		border-radius: 5px;
	}
</style>
