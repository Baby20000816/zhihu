<template>
	<div class="row">
		<!-- <div class="container">
			<div class="row" v-for="(item,index) in specials" :key="index">
				<div class="col-4">
					<img :src="item.banner" alt="" />
				</div>
				<div class="col-8">
					<h3>{{item.title}}</h3>
					<p class="meta">{{item.updated}}更新，{{item.viewCount}}次浏览</p>
					<p class="introduction">{{item.introduction.slice(0, 20)}}...</p>
				</div>
			</div>
		</div> -->
		<div class="col-10">
			<div v-for="(item, index) in specials.slice(0,count)" :key="index" class="col-12">
				<div class="media-wraaper ">
					<div class="col-4">
						<img :src="item.banner" class="reimg" />
					</div>
					<div class="media-middle flex flex-around flex-left">
						{{item.title}}
						<p class="sub-title link">{{item.introduction.slice(0, 20)}}...</p>
						<p>
							<span class="meta gutter">{{item.updated}}更新</span>
							<span class="meta">{{item.viewCount}}浏览</span>
						</p>
					</div>
				</div>
			</div>
		</div>
	<!-- 	<div class="col-4">

			<div class="col-12 border box">

			</div>
		</div> -->
	</div>
</template>

<script>
	export default {
		name: 'recommoned',
		data() {
			return {
				specials: [],
				count: 5,
				scroll: '',
				win:0
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/special/all').then(res => {
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
	.reimg {
		display: flex;
		align-items: center;
		width: 100%;
		height: 80%;
	}

	.container {
		.row {
			display: flex;
			margin-bottom: 10px;

			border: 1px solid #d6d6d6;
			border-radius: 4px;
			height: 180px;
			padding: 14px;
			box-shadow: 0 1px 3px 0 rgba(26, 26, 26, 0.1);

			.col-4 {
				flex: 0 0 33%;
				height: 100%;

				img {
					width: 100%;
					height: 100%;
					border-radius: 10px;
				}
			}

			.col-8 {
				flex: 0 0 66%;
				text-align: left;
				line-height: 28px;
				padding-left: 15px;

				h3 {
					font-weight: 700;
				}

				.meta {
					font-size: 13px;
					color: #99a6c4;
				}

				.introduction {
					font-size: 15px;
				}

				.section {
					background-color: #eee;
					padding: 3px;
					margin: 5px;
				}
			}
		}
	}
</style>
