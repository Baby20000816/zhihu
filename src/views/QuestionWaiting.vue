<template>
	<div class="container">
		<li class="nav-item">
			<router-link to="/home"><p class="zhihu">123</p></router-link>
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
		
	</div>
</template>

<script>
	export default {
		name:'recommoned',
		data(){
			return {};
		},
		created() {
			
		}
	};
</script>

<style lang="scss" scoped>
</style>
