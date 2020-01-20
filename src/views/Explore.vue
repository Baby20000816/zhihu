<template>
	<div>
		<div class="containerzhihu">
			<h2>最新专题</h2>
			<div class="box-card flex col-12">
				<div class="row-card" v-for="(item,index) in specials.slice(0,4)" :key="index">
					<div class="card-box">
						<div class="">
							<img :src="item.banner" alt="" />
						</div>
						<div class="col-8">
							<h3>{{item.title}}</h3>

							<p>
								<span class="meta gutter">{{item.updated}}更新</span>
								<span class="meta">{{item.viewCount}}浏览</span>
							</p>
							<hr>
							<p class="sub-title link">{{item.introduction.slice(0, 20)}}...</p>
						</div>
					</div>
				</div>
			</div>
			<p class="buttum-position">
				<router-link to="/special/all">查看更多专题</router-link>
			</p>
		</div>
		<div class="containerzhihu1">
			<h2>圆桌讨论</h2>
			<div class="box-card flex col-12">
				<div class="row-card" v-for="(items,index) in roundtable.slice(0,4)" :key="index">
					<div class="card-box">
						<div class="background-size" v-bind:style="{ 'background-image': 'url(' + items.tinyBanner + ')','background-repeat':'no-repeat','background-size':'cover'}">
							<!-- <img :src="items.banner" alt="" /> -->
							<h3>{{items.name}}</h3>

							<p>
								<!-- <span class="meta gutter">{{items.updated}}更新</span> -->
								<span class="meta">{{items.visitsCount}}浏览</span>
							</p>
							<p class="sub-title link">{{items.includeCount}}位嘉宾参与</p>
						</div>
						<div class="col-8">
							<h3>{{items.name}}</h3>

							<p>
								<!-- <span class="meta gutter">{{items.updated}}更新</span> -->
								<span class="meta">{{items.visitsCount}}浏览</span>
							</p>
							<hr>
							<p class="sub-title link">{{items.includeCount}}位嘉宾参与</p>
						</div>
					</div>
				</div>
			</div>
			<p class="buttum-position">
				<router-link to="/roundtable">圆桌讨论</router-link>
			</p>
		</div>

		<div class="containerzhihu1">
			<h2>收藏夹</h2>
			<div class="box-card1 flex col-12">
				<div class="row-card1" v-for="(items,indexs) in favorite.slice(0,4)" :key="indexs">
					<div class="card-box1">
						<h3>{{items.title}}</h3>
						<div>
							<img :src="items.creatorAvatar" alt="" />
							{{items.creatorName}}创建 {{items.followers}}人关注
							<hr>
						</div>
						<div class="col-8" >
							<p>{{items.questionTitle}}</p>
							<p>{{items.answerAuthorName}}:{{items.answerContent.slice(0,20)}}...</p>
							<p>回答  {{items.voteupCount}}人赞同·{{items.commentCount}}人评论</p>
							<p>已收藏{{items.totalCount}}条内容</p>
						</div>
					</div>
				</div>
			</div>
			<p class="buttum-position1">
				<router-link to="/favorite">收藏夹</router-link>
			</p>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'explore',
		data() {
			return {
				specials: [],
				roundtable: [],
				favorite: [],
				user: [],
				count: 5,
				start: 0,
				end: 2,
				scroll: ''
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/special').then(res => {
				console.log(res);
				this.specials = res.data.data;
			})
			this.axios.get('http://localhost:8080/api/roundtable/all').then(res => {
				console.log(res);
				this.roundtable = res.data.data;
			})
			this.axios.get('http://localhost:8080/api/user').then(res => {
				console.log(res);
				this.user = res.data.data;
			})
			this.axios.get('http://localhost:8080/api/favorite').then(res => {
				console.log(res);
				this.favorite = res.data.data;
			})
		},
		methods: {
			loadMore() {
				this.count = this.count + 5
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
	.banner {
		border: 1px solid #d6d6d6;
		box-shadow: 2px 5px 5px #ddd;
		padding-left: 10%;
		display: flex;
		align-items: center;

		.img {
			height: 60%;
		}
	}

	.pictures {
		img{
			width: 10px;
			height: 10px;
		}
	}

	.background-size {
		// width: 100%;		 // height: 100%;
		width: 100%;
		height: 200px;

	}

	.box-card {
		display: flex;
		width: 60%;
		height: 300px;

		.row-card {
			border: 1px solid #DDDDDD;
			box-shadow: 1px 1px 1px #aaa;
			width: 501px;
			// height: 180px;
			background-color: white;
			border-radius: 5px;
			padding: 10px;
			margin-bottom: 10px;
			margin-right: 10px;

			.card-box {
				margin-left: -10px;
				margin-top: -10px;
				width: 500px;

				img {
					// width: 490px;
					border-top-left-radius: 5px;
					border-top-right-radius: 5px;
					width: 100%;
					height: 200px;
				}
			}
		}

	}
	.box-card1 {
		display: flex;
		width: 60%;
		height: 300px;
	
		.row-card1 {
			border: 1px solid #DDDDDD;
			box-shadow: 1px 1px 1px #aaa;
			width: 501px;
			// height: 180px;
			background-color: white;
			border-radius: 5px;
			padding: 10px;
			margin-bottom: 10px;
			margin-right: 10px;
	
			.card-box1 {
				margin-left: -10px;
				margin-top: -10px;
				width: 500px;
	
				img {
					// width: 490px;
					border-top-left-radius: 5px;
					border-top-right-radius: 5px;
					width: 20px;
					height: 20px;
				}
			}
		}
	
	}

	.containerzhihu {
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
	.buttum-position1{
		margin-top: 10px;
		margin-bottom: auto;
		margin-left: auto;
		margin-right: auto;
		cursor: pointer;
		border: 2px solid #DDDDDD;
		border-radius: 10px;
		background-color: white;
		font-size: 10px;
	}
</style>
