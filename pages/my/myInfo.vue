<template>
	<view class="uni-tab-bar">
		<view class="infoCard">
			<view class="infoCard-top">
			  <view class="headProtrait">
			  <image src="../../static/headProtrait.jpeg"></image>
			  </view>
			  <navigator url="userInfo/userInfo">
				  <button type="primary">编辑资料</button>
			  </navigator>
			</view>
			<view style="text-indent:1em; margin-top:10upx;">{{userName}}<span style="font-size:15upx; color:#BAC1C2">-{{studentId}}</span></view>
			<view class="follow">
				<span style="color:#00A0F3">{{following}}</span>我关注的
			    <span style="color:#00A0F3">{{follower}}</span>关注我的
			</view>
		</view>
		<view class="uni-swiper-tab">
			<view v-for="(tab,index) in tabBars" :key="index" class="swiper-tab-list" :class="tabIndex==index ? 'active' : ''"
			  :data-current="index" @click="tapTab">
			 {{tab.name}} {{tab.num}}</view>
		</view>
		<scroll-view class="list" scroll-y @scrolltolower="loadMore(tab_index)">
			    <navigator url="../question/question">
					<yz-content-card class="cards1" v-for="(t,i) in 3"  title="问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题问题" note="用户 A"  time="3天前" browse="2500" reply="50" collect="3" >
						谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 
					</yz-content-card>
				</navigator>	
					<uni-load-more :status="status" :content-text="contentText" color="#007aff" />
		</scroll-view>
	</view>
</template>

<script>
	import yzContentCard from '@/components/youzhi/yz-content-card.vue'
	import uniLoadMore from '@/components/uni-load-more/uni-load-more.vue'
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	export default{
		components:{
			yzContentCard,uniLoadMore,uniList,uniListItem
		},
		data(){
			return{
				userName: '王大锤',
				studentId: 'B19010101',
				follower: 5,
				following: 26,
				tabIndex: 0,
				isClickChange: false,
				tabBars:[
					  {
						name: '关注',
						num: '3'
					  },{
						name: '提问',
						num: '2'
					  },{
						name: '回答',
						num: '1'
					  },{
						name: '文章',
						num: '0'
					  },
				],
				status: 'more',
				statusTypes: [{
					value: 'more',
					text: '加载前',
				}, {
					value: 'loading',
					text: '加载中',
				}, {
					value: 'noMore',
					text: '没有更多',
				}],
				contentText: {
					contentdown: '查看更多',
					contentrefresh: '加载中',
					contentnomore: '没有更多'
				}
			}
		},
		methods:{
			 async tapTab(e) { //点击tab-bar
				let tabIndex = e.target.dataset.current;
				// if (this.newsitems[tabIndex].data.length === 0) {
				// 	this.addData(tabIndex)
				// }
				if (this.tabIndex === tabIndex) {
					return false;
				} else {
					this.isClickChange = true;
					this.tabIndex = tabIndex;
				}
			},
		}
	}
</script>

<style scoped>
	.infoCard{
		background-color: #FFF;
		height:300upx;
		border-top-left-radius:50%;
		border:1upx solid #BAC1C2;
		margin-top:50upx;
	}
	.infoCard-top{
		overflow:hidden;
		positon:relative;
	}
	.infoCard button{
		width:200upx;
		font-size:30upx;
		display:block;
		float:right;
		margin-right:50upx;
		margin-top:100upx;
	}
	.headProtrait{
		width:210upx;
		height:210upx;
		border-radius:50%;
		border: 2upx solid #BAC1C2;
		float:left;
		position: absolute;
		top:-30upx;
	}
	.headProtrait image{
		width:200upx;
		height:200upx;
		border-radius:50%;
		display:block;
		margin:5upx;
	}
	.follow{
		font-size:30upx; 
		color:#889596;
		line-height:50upx;
	}
	.follow span{
		padding-left:15upx;
	}
	.uni-swiper-tab {
		width: 100%;
		height:100upx;
		border-bottom: 1upx solid #c8c7cc;
		border-top: 1upx solid #c8c7cc;
	}
	.swiper-tab-list {
		padding:0upx 25upx;
		font-size: 30upx;
	    display:inline-block;
		text-align: center;
		color: black;
		line-height:100upx;
		background-color: #FFF;
	}
	.active {
		color: #007AFF;
		border-bottom: 3upx solid #007AFF;
	}
	.cards1{
		Width:100%;
		margin-top: 20upx;
		border:1upx solid #DCDCDC;
		box-shadow:0px 0px 0px #FAFAFA;
	}
</style>
