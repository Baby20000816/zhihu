<template>
	<div class="roundtable">
		<!-- <div class="col-12"> -->
			<div class="containerroundtable">
				<div class="" v-for="(item,index) in specials.slice(1,count)" :key="index">
					<div class="backgroundsize" v-bind:style="{ 'background-image': 'url(' + item.banner + ')','background-repeat':'no-repeat','background-size':'cover'}">
							<p class="backgroundsize-font">{{item.name}}</p>
					</div>
					<div class="font">
							该圆桌被浏览{{item.visitsCount}}次
						</span>
					</div>
				</div>
			<!-- </div> -->
		</div>
	</div>
</template>

<script>
	export default {
		name: 'roundtable',
		data() {
			return {
				specials: [],
				count: 9,
				scroll: '',
				
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/roundtable/all').then(res => {
				console.log(res);
				this.specials = res.data.data;
			})
		},
		methods: {
			loadMore() {
							this.count=this.count+5
							this.win=1
						},
			scrollDs() {
				//变量scrollTop是滚动条滚动时，距离顶部的距离
				var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
				//变量windowHeight是可视区的高度
				var windowHeight = document.documentElement.clientHeight || document.body.clientHeight;
				//变量scrollHeight是滚动条的总高度
				var scrollHeight = document.documentElement.scrollHeight || document.body.scrollHeight;
				//滚动条到底部的条件
				if (scrollTop + windowHeight >= scrollHeight) {
					//到了这个就可以进行业务逻辑加载后台数据了
					this.loadMore();
				}
			}
		},
		mounted() {
			window.addEventListener('scroll', this.scrollDs);
		}
	}
</script>

<style lang="scss" scoped>
	.roundtable{
		width: 1000px;
		position: absolute;
		left: 400px;
		top: 100px;
		background-color: white;
	}
	.containerroundtable {
		width: 100%;
		display: flex;
		flex-wrap: wrap;
		 // margin: 0 auto;
		margin-top: 100px;
		margin-bottom: auto;
		margin-left: auto;
		margin-right: auto;
	}
	.backgroundsize{
		width: 200px;
		height: 200px;
		margin-right: 15px;
		margin-left: 30px;
		margin-bottom: 10px;
		border-radius: 10px;
	}
	.backgroundsize-font{
		position: relative;
		top: 170px;
		right: -10px;
		font-size: 16px;
		color: rgb(255, 255, 255);
	}
	.font{
		position: relative;
		left: 30px;
		font-size: 12px;
		color: rgb(133, 144, 166);
		margin-bottom: 50px;
	}
</style>
