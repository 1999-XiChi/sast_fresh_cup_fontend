<template>
	<view>
		<view class="infoCard">
		  <view class="infoCard-top">
			 <view class="headProtrait">
			   <image src="../../static/headProtrait.jpeg"></image>
			 </view>
			 <view class="moreInfo">
				 <view class="name">
				 	{{userName}}<p>{{studentId}}</p>
				 </view>
			 		<navigator url="/pages/my/myInfo">
			 				<view style="line-height:80upx;" v-show="LandingStatus">个人主页></view>
			 		</navigator>
			 </view>
		  </view>
		  <div class="link-top"></div>
		  <view class="infoCard-bottom">
			  <p class="link-right">我的创作<span>|</span></p>
		      <p class="link-right">我的关注<span>|</span></p>
		      <p class="link-right">收藏夹<span>|</span></p>
		  </view>
		</view>	
		<view v-show="!LandingStatus" class="welcome_parts">
			<view style="text-align: center;">登录柚知，体验更多功能</view>
			<image src="../../static/thumbnail.jpg" class="welcome"></image>
			<navigator url="/pages/auth/signIn" hover-class="navigator-hover">
				<button class="yz-button" type="default" style="background-color:#5C9857;color:white;letter-spacing:10upx;">登录</button>
			</navigator>
			<navigator url="/pages/auth/signUp" hover-class="navigator-hover">
				<button class="yz-button" type="default" style="background-color:#C56852; color:white;letter-spacing:10upx;">注册</button>
			</navigator>
		</view>
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
				LandingStatus: false,
				userName: '未登录',
				studentId: 'B19010101'
			}
		},
		onLoad() {
		},
		methods: {

		}
	}
</script>

<style>
	//infocard
	.infoCard{
		width:80%;
		margin:10upx auto;
		box-shadow: 0upx 0upx 10upx #6E826C;
		border-radius:10upx;
		padding:20upx;	
	}
	.infoCard-top{
		overflow:hidden;
	}
	.moreInfo{
		display:flex;
		justify-content:space-between;
		float:left;
		padding-top:90upx;
		width:380upx;
		font-size:25upx;
		line-height:25upx;
		color:#8B9B8A;
	}
	.moreInfo .name{
		line-height:50upx;
		padding-left: 20upx;
		font-size:40upx;
		color:#000000;
	}
	.moreInfo .name p{
		font-size:20upx;
		color:#BAC1C2;
	}
	.headProtrait{
		width:210upx;
		height:210upx;
		border-radius:50%;
		border: 2upx solid #BAC1C2;
		overflow:hidden;
		float:left;
	}
	.headProtrait image{
		width:200upx;
		height:200upx;
		border-radius:50%;
		display:block;
		margin:5upx;
	}
	.infoCard-bottom{
		overflow:hidden;
		line-height:100upx;
	}
	//横线
	.link-top {
	      width: 100%;
	      height: 15upx;
	      border-bottom: solid #ACC0D8 1upx;
	   }
	//竖线
	.link-right {
		display:block;
		float:left;
		width:33%;
		text-align:center;
		font-size:30upx;
	}
	.link-right span{
		padding-left:35upx;
		font-size:40upx;
		color:#4CB1E5;
	}
	//原来的内容
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
	.welcome{
		width:300upx;
		height:300upx;
		display:block;
		margin:10upx auto;	
		border-radius:55upx;
		opacity:0.8;
	}
	.welcome_parts{
		width:80%;
		margin:50upx auto;
	}
</style>
