<template>
	<div>
		<div class="nav gutter shadow">
			<div class="nav-bar nav-bar-fixed shadow">
				<ul class="nav-list flex-center">
					<li class="nav-item">
						<router-link to="/home"><p class="zhihu">知乎</p></router-link>
					</li>
					<li class="nav-item">
						<router-link to="/home">主页</router-link>
					</li>
					<li class="nav-item">
						<router-link to="/explore">发现</router-link>
					</li>
					<li class="nav-item">
						<router-link to="/question/waiting">等你来答</router-link>
					</li>
					<li class="nav-item abs-center-right">
						<router-link to="/login">登录</router-link>
					</li>
				</ul>
			</div>
		</div>
		<!-- 二级路由入口 -->
		<router-view />
	</div>
</template>

<script>
	export default {
		name: 'nav',
		data() {
			return {};
		},
		created() {

		}
	};
</script>

<style lang="scss" scoped>
	
	.zhihu{
		font-size: 26px;
		color: rgb(32, 147, 255);
	}
	.router-link-active {
		border-bottom: 2px;
		border-bottom-color:rgb(0, 132, 255);
		color: #000000;
	}
	.gutter {
		position: relative;
		margin-bottom: 10px;
	}
	.container {
		margin-top: 90px;
	}

	.red {
		background-color: #9CCC65;
		color: #DDDDDD;
	}

	.meta {
		font-size: 13px;
		color: black;
	}

	.nav-item {
		color: black;
		height: 80px;
		line-height: 70px;
	}
	.nav-bar-fixed {
		position: fixed;
		top: 0px;
		width: 100%;
		background-color: white;
	}

	.nav-item input {
		margin-top: 15px;
		width: 200px;
		height: 35px;
	}

	.nav-item img {
		width: 45px;
		height: 45px;
		border-radius: 50%;
	}

	.nav-item a {
		display: inline-block;
		width: 80px;
		height: 35px;
		margin-right: 5px;
		font-size: 15px;
		color: rgb(133, 144, 166);
		text-align: center;
		line-height: 35px;
		letter-spacing: 3px;
	}
</style>
