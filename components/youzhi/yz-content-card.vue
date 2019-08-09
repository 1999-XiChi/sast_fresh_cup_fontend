<template>
	<view class="content-card" @click="onClick">
		<view v-if="title" class="content-card-header">
			<view class="uni-card__header-title-text">{{ title }}</view>
			<view v-if="extra" class="uni-card__header-extra-text">
			{{ extra }}
			</view>
		</view>
		<view class="content-card-body">
			<view :class="thumbnail?'content-slot':'content-slot-entire'">
				<slot></slot>
			</view>
			<view v-if="thumbnail" class="uni-card__header-extra-img-view">
				<image :src="thumbnail" class="uni-card__header-extra-img" />
			</view>
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
			   <view class="flex-wrp" style="flex-direction:row;">
               <view class="flex-item">{{browse}} 浏览</view>
               <view class="flex-item">{{reply}} 回复</view>
               <view class="flex-item">{{collect}} 收藏</view>
            </view>
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
			thumbnail:{
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
	.down .flex-item{
		display:block;
		float:left;
		font-size:20upx;
	}	
	.down .flex-item:nth-child(1){
		padding-right:35upx;
	}
	.down .flex-item:nth-child(3){
		float:right;
		padding-right:5upx;
	}
    .content-slot{
		display:block;
		float:left;
		width:59%;
		text-indent:2em; 
		margin-right:5upx;
		display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 6;
        overflow: hidden;
	}
	.content-slot-entire{
		display:block;
		float:left;
		width:100%;
		text-indent:2em; 
		margin-right:5upx;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 3;
		overflow: hidden;
	}
    .uni-card__header-extra-img-view{
	    display:block;
	    float:right;
	    width:40%;
	    height:200upx;
   }
	.uni-card__header-extra-img{
		width:100%;
		height:200upx;
		border-radius:20upx;
		opacity:0.7;
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
