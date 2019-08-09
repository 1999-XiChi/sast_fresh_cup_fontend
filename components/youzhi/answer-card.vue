<template>
	<view class="card" @click="onClick">
		<view class="body">
			<view class="content-pic">
				<image src="../../static/headProtrait.jpeg"></image>
				<image src="../../static/headProtrait.jpeg"></image>
				<image src="../../static/headProtrait.jpeg"></image>
			</view>
			<slot />
		</view>
		<view class="footer">
		   <view>
			    <image class="avatar" :src="avatar"></image>
				<p class="text"> {{username}} · {{agree}}  <i class="fa fa-thumbs-up"></i> · {{comment}}  <i class="fa fa-comments"></i> · {{favor}} <i class="fa fa-star"></i> · {{time}} <i class="fa fa-clock-o"></i></p>
		   </view> 
		</view>	
	</view>
</template>

<script>
	export default {
		name: 'answerCard',
		props: {
			avatar: {
				type: String,
				default: '../../static/headProtrait.jpeg'
			}, // 头像
			username: {
				type: String,
				default: '用户名'
			}, // 扩展信息
			agree: {
				type: Number,
				default: 0
			}, // Tips
			comment:{
				type:Number,
				default: 0
			},
			favor: {
				type: Number,
				default: 0
			}, 
			time:{
				type:String,
				default: '刚刚'
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
	.card{
		border-radius: 24upx;
		background-color: #FFFEFE;
		margin: 16upx 0;
	}
	.card:first-of-type{
		margin-top: 0;
	}
	
	.avatar{
		width: 50upx;
		height: 50upx;
		border-radius: 50%;
	}
	.footer{
		margin: 12upx;
		padding-top: 4upx;
		border-top: 1px solid rgba(0, 0, 0, 0.15);
		color: #A7A7A7;
	}
	.text{
		font-size: 28upx;
		margin-left: 10upx;
		display: inline;
		vertical-align: super;
	}
	
	.body{
		color: #444444;
		padding: 12upx;
		font-size: 28upx;
		overflow : hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 4;
		-webkit-box-orient: vertical;
	}
	.content-pic{
		display: flex;
	}
	.content-pic > image {
		border-radius: 8upx;
		margin: 1upx;
		height: 150upx;
		flex-flow: column;
		object-fit: cover;
	}
</style>
