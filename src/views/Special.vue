<template>
	<div class="col-4">
		<!-- <div class="banner">
			<img src="../assets/logo.png" alt="" />
			<h3>全部专题</h3>
		</div> -->
		<div class="containerzhihu">
			<div class="row" v-for="(item,index) in specials" :key="index">
				<div class="col-4">
					<img :src="item.banner" alt="" />
				</div>
				<div class="col-8">
					<h3>{{item.title}}</h3>
					<p class="meta">{{item.updated}}更新，{{item.viewCount}}次浏览</p>
					<p class="introduction">{{item.introduction.slice(0,50)}}...</p>
					<br>
					<span class="section" v-for="(section,index) in item.sections" :key="index">
						{{section.sectionTitle}}
					</span>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'favorite',
		data() {
			return {
				specials: []
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/favorite').then(res => {
				console.log(res);
				this.specials = res.data.data;
			})
		}
	}
</script>

<style lang="scss" scoped>
	.banner{
		border: 1px solid #d6d6d6;
		box-shadow: 2px 5px 5px #ddd;
		padding-left: 10%;
		display:flex;
		align-items: center;
		img{
			height: 60%;
		}
	}
	.containerzhihu{
		.row{
			display: flex;
			margin-bottom: 10px;
			border: 1px solid #d6d6d6;
			border-radius: 4px;
			height: 180px;
			padding: 14px;
			box-shadow: 0 1px 3px 0 rgba(26,26,26,0.1);
			.col-4{
				flex:  0 0 33%;
				height: 100%;
				img{
					width: 100%;
					height: 100%;
					border-radius:10px ;
				}
			}
			.col-8{
				flex: 0 0 66%;
				text-align: left;
				line-height: 28px;
				padding-left: 15px;
				h3{
					font-weight: 700;
				}
				.meta{
					font-size: 13px;
					color: #99a6c4;
				}
				.introduction{
					font-size: 15px;
				}
				.section{
					background-color: #eee;
					padding: 3px;
					margin: 5px;
					size: 14px;
					font-size: 14px;
				}
			}
		}
	}
</style>
