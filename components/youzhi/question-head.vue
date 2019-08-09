<template>
	<view class="title">
		<h3>{{title}}</h3>
		<slot />
		<small>{{focus}} 人关注 · {{answerCount}} 个回答</small>
		<view class="action">
			<button><i class="fa fa-bullseye"></i>关注问题</button>
			<button><i class="fa fa-user-plus"></i>邀请回答</button>
			<button><i class="fa fa-pencil-square-o"></i>写一回答</button>
		</view>
	</view>
</template>

<script>
	export default{
		name:'questionCapital',
		props: {
			title: {
				type: String,
				default: '问题标题'
			},
			focus: {
				type: Number,
				default: 0
			},
			answerCount: {
				type: Number,
				default: 0
			},
		},
	}
</script>

<style>
	.title{
		background-color: #FFFEFE;
		font-size: 32upx;
		margin: 12upx;
		color: #1A1A1A;
	}
	.title > small{
		margin-top: 16upx;
		font-size: 22upx;
		display: block;
	}
	.action{
		margin-top: 24upx;
		display: flex;
		
	}
	.action > button{
		color: #101010;
		font-size: 28upx;
		width: 30%;
	}
	button:after{
		border: 0;
	}
</style>
