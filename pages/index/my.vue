<template>
	<view>
		<uni-list>
			<uni-list-item :title="userName" :note="studentId" thumb="https://img-cdn-qiniu.dcloud.net.cn/new-page/uni.png" />
		</uni-list>	
		<view class="example-title">账户相关</view>
		<uni-list>
			<uni-list-item title="我的提问"/>
			<uni-list-item title="我的回答"/>
			<uni-list-item title="收藏"/>
		</uni-list>	
		<navigator url="/pages/auth/signIn" hover-class="navigator-hover">
			<button class="yz-button" type="default">登录</button>
		</navigator>
		<navigator url="/pages/auth/signUp" hover-class="navigator-hover">
			<button class="yz-button" type="default">注册</button>
		</navigator>
	</view>
</template>

<script>
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	export default {
		components:{
			uniList, uniListItem
		},
		data() {
			return {
				userName: '未登录',
				studentId: '-'
			}
		},
		onLoad() {
		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
	.example-title {
		font-size: 24upx;
		line-height: 24upx;
		color: #777;
		margin: 20upx 25upx;
		position: relative
	}
</style>
