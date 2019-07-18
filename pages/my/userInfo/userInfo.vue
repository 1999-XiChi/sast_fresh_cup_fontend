<template>
	<view>
		<uni-list>
			<uni-list-item title="头像" note="-" thumb="https://img-cdn-qiniu.dcloud.net.cn/new-page/uni.png" />
		</uni-list>	
		
		<uni-list>
			<uni-list-item title="昵称" note=""/>
			<uni-list-item title="学号" note=""/>
			<uni-list-item title="真实姓名" note=""/>
			<uni-list-item title="性别" note=""/>
			<uni-list-item title="年级" note=""/>
			<uni-list-item title="专业" note=""/>
		</uni-list>	
		<navigator url="/pages/public/signIn" hover-class="navigator-hover">
			<button class="yz-button" type="default">退出登录</button>
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
		methods: {
			
		}
	}
</script>

<style>

</style>
