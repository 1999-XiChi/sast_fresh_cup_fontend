<template>
	<view class="content-card" @click="onClick">
		<view v-if="title" class="content-card-header">
			<view v-if="thumbnail" class="uni-card__header-extra-img-view">
				<image :src="thumbnail" class="uni-card__header-extra-img" />
			</view>
			<view class="uni-card__header-title-text">{{ title }}</view>
			<view v-if="extra" class="uni-card__header-extra-text">
			{{ extra }}
			</view>
		</view>
		<view class="content-card-body">
			<slot />
		</view>
		<view class="content-card-footer">
		   <view class = 'up'>
			    <image src="../../static/headProtrait.jpeg"></image>  
			   {{ note }}
			   <view class="timeTip">
			   	{{time}}
			   </view>	   
		   </view> 
		   <view class = "down">
			<li>{{browse}} 浏览</li>
			<li>{{reply}} 回复</li>
			<li>{{collect}} 收藏</li>
		  </view>
		</view>	
	</view>
</template>

<script>
	export default {
		name: 'UniCard',
		props: {
			title: {
				type: String,
				default: ''
			}, // 标题
			extra: {
				type: String,
				default: ''
			}, // 扩展信息
			note: {
				type: String,
				default: ''
			}, // Tips
			time: {
				type: String,
				default: ''
			}, 
			browse:{
				type:String,
				default: ''
			},
			reply:{
				type:String,
				default: ''
			},
			collect:{
				type:String,
				default: ''
			},
			thumbnail: {
				type: String,
				default: ''
			}, // 缩略图
			isFull: { // 内容区域是否通栏
				type: Boolean,
				default: false
			}
		},
		methods: {
			onClick() {
				this.$emit('click')
			}
		}
	}
</script>

<style>
	*{
		box-sizing:border-box;
	}
	.content-card {
		padding: 16upx 16upx 0 16upx;
		background: #fff;
		position: relative;
		flex-direction: column;
		box-shadow: rgba(0, 0, 0, 0.1) 5px 5px 6px;
		border-buttom: 1upx solid rgba(0, 0, 0, 0.15);
		overflow:hidden;
	}

	.content-card-header{
		font-size: 32upx;
		overflow : hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
	}
	.content-card-body{
		font-size: 24upx;
		overflow : hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 4;
		-webkit-box-orient: vertical;
		color: #555555;
	}
	.content-card-footer{
		justify-content: space-between;
		overflow: hidden;
		color: #999;
		font-size: 24upx;
		padding-bottom: 5upx;
	}
	.up{
		height:50upx;
		line-height:50upx;
	}
	.up image{
		display:block;
		float:left;
		width:50upx;
		height:50upx;
		border-radius:50upx;
		margin-right:15upx;
		}
	.up .timeTip{
		float:right;
		margin-right:5upx;
	}
	.down{
		list-style: none;
		overflow:hidden;
		line-height:50upx;
		background-color: #FFFFFF;
		color:#3F536E;
        border-top:1upx solid rgba(0, 0, 0, 0.15);
		margin-top:10upx;
	}
	.down li{
		display:block;
		float:left;
		font-size:10upx;
	}	
	.down li:nth-child(1){
		padding-right:35upx;
	}
	.down li:nth-child(3){
		float:right;
		padding-right:5upx;
	}
/* 	.uni-card__footer,
	.uni-card__header {
		position: relative;
		display: flex;
		flex-direction: row;
		padding: 8upx;
		align-items: center
	}

	.uni-card__header:after {
		position: absolute;
		bottom: 0;
		right: 0;
		left: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc
	}

	.uni-card__header-title {
		flex: 1;
		margin-right: 16upx;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center
	}

	.uni-card__header-extra-img-view {
		display: flex
	}

	.uni-card__header-extra-img {
		height: 40upx;
		width: 40upx;
		margin-right: 16upx
	}

	.uni-card__header-extra-text {
		flex: 0 0 auto;
		width: 30%;
		margin-left: 16upx;
		font-size: 28upx;
		text-align: right;
		text-overflow: ellipsis;
		white-space: nowrap;
		overflow: hidden
	}

	.uni-card__content--pd {
		padding: 16upx
	}

	.uni-card__footer {
		
	} */

</style>
