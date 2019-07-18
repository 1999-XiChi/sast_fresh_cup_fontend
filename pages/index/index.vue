<template>
	<view>
		<view class="uni-tab-bar">
			<view class="uni-swiper-tab">
				<view v-for="(tab,index) in tabBars" :key="tab.id" class="swiper-tab-list" :class="tabIndex==index ? 'active' : ''"
				 :id="tab.id" :data-current="index" @click="tapTab">{{tab.name}}</view>
			</view>
			<scroll-view class="list" scroll-y @scrolltolower="loadMore(tab_index)">
						<yz-content-card class="cards1" v-for="(t,i) in 3" title="问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 问题题目 " note="用户 A 3天前" >
							这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 这个是内容 
						</yz-content-card>
						<view class="uni-tab-bar-loading">
							载入中 
						</view>
			</scroll-view>
		</view>
		<uni-fab class="index-fab" ref="fab" :pattern="pattern" :content="content" 
		horizontal="right" vertical="bottom" direction="vertical" @trigger="trigger" />
	</view>
</template>

<script>
	import uniFab from '@/components/uni-fab/uni-fab.vue'
	import yzContentCard from '@/components/youzhi/yz-content-card.vue'

	export default {
		components: {
			uniFab, yzContentCard
		},
		data() {
			return {
				scrollLeft: 0,
				isClickChange: false,
				tabIndex: 0,
				newsitems: [],
				tabBars: [{
					name: '推荐',
					id: 'tuijian'
				},{
					name: '关注',
					id: 'guanzhu'
				}],
				pattern: {
					color: '#7A7E83',
					backgroundColor: '#fff',
					selectedColor: '#007AFF',
					buttonColor: '#007AFF'
				},
				content: [{
						iconPath: '/static/component.png',
						selectedIconPath: '/static/componentHL.png',
						text: '组件',
						active: false
					},
					{
						iconPath: '/static/api.png',
						selectedIconPath: '/static/apiHL.png',
						text: 'API',
						active: false
					},
					{
						iconPath: '/static/template.png',
						selectedIconPath: '/static/templateHL.png',
						text: '模版',
						active: false
					}
				]
			}
		},
		onLoad() {
			this.newsitems = this.randomfn()
		},
		methods: {
			goDetail(e) {
				
			},
			close(index1, index2) {
				
			},
			loadMore(e) {
				setTimeout(() => {
					this.addData(e);
				}, 1200);
			},
			addData(e) {
				
			},
			async changeTab(e) {
				let index = e.target.current;
                this.tabIndex = index;
				if (this.newsitems[index].data.length === 0) {
					this.addData(index)
				}
				if (this.isClickChange) {
					this.isClickChange = false;
					return;
				}
				let tabBar = await this.getElSize("tab-bar"),
					tabBarScrollLeft = tabBar.scrollLeft;
				let width = 0;

				for (let i = 0; i < index; i++) {
					let result = await this.getElSize(this.tabBars[i].id);
					width += result.width;
				}
				let winWidth = uni.getSystemInfoSync().windowWidth,
					nowElement = await this.getElSize(this.tabBars[index].id),
					nowWidth = nowElement.width;
				if (width + nowWidth - tabBarScrollLeft > winWidth) {
					this.scrollLeft = width + nowWidth - winWidth;
				}
				if (width < tabBarScrollLeft) {
					this.scrollLeft = width;
				}
				this.isClickChange = false;
			},
			getElSize(id) { //得到元素的size
				return new Promise((res, rej) => {
					uni.createSelectorQuery().select("#" + id).fields({
						size: true,
						scrollOffset: true
					}, (data) => {
						res(data);
					}).exec();
				})
			},
			async tapTab(e) { //点击tab-bar
				let tabIndex = e.target.dataset.current;
				if (this.newsitems[tabIndex].data.length === 0) {
					this.addData(tabIndex)
				}
				if (this.tabIndex === tabIndex) {
					return false;
				} else {
					this.isClickChange = true;
					this.tabIndex = tabIndex;
				}
			},
			randomfn() {
				let ary = [];
				return ary;
			},
			trigger(e) {
				console.log(e)
			}
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
	.uni-tab-bar {
		background-color: #E3F4E3;
		flex-direction: column;
		overflow: hidden;
		height: 100%;
	}
	.uni-tab-bar .list {
		width: 750upx;
		height: 100%;
	}
	.uni-swiper-tab {
		width: 100%;
		line-height: 100upx;
		border-bottom: 1px solid #c8c7cc;
		text-align: center;
	}
	.swiper-tab-list {
		font-size: 30upx;
		width: 150upx;
		display: inline-block;
		text-align: center;
		color: black;
	}
	.uni-tab-bar .active {
		color: #007AFF;
		border-bottom: 2upx solid #007AFF;
	}
.list{
	background-color: #FAFAFA;
}
.uni-tab-bar-loading{
	padding:20upx 0;
}
.cards1{
	margin: 24upx;
}
</style>

