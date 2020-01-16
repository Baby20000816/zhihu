<template>
	<div class="home shadow">
		<div class="gutter">
			<div class="td-box">
				<ul class="nav-list flex-left">
					<li>
						<router-link :to="{ path: 'recommoned'}">  <span class="one">推荐</span>  </router-link>
					</li>
					
					<li>
						<router-link :to="{ path: 'follow'}"> <span class="one">关注</span>  </router-link>
					</li>
					<li>
						<router-link :to="{ path: 'hot'}"> <span class="one">热榜</span>  </router-link>
					</li>
				</ul>
				<hr class="hr">
			</div>
		</div>
		<!-- 二级路由入口 -->
		<router-view />
	</div>
</template>

<script>
	export default {
		name: 'home',
		data() {
			return {
				specials: []
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/special/all').then(res => {
				console.log(res);
				this.specials = res.data.data;
			})
		}
	}
</script>
<style lang="scss" scoped>
	.one{
		display: flex;
		position: relative;
		
	}
	.hr{
		position: absolute;
		
	}
	.td-box{
		border: 2px 2px 2px 2px;
	}
	.home{
		width: 800px;
		position: absolute;
		left: 400px;
		top: 100px;
		background-color: white;
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

	.nav-item {
		color: black;
		height: 50px;
		line-height: 70px;
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
