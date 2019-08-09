<template>
	<view>
		<view>
		<question-head title="如何评价孙笑川">有人说他是无恶不作，新津暴徒，文艺复兴，工地英语，儒雅随和，你怎么看？</question-head>
		</view>
		<scroll-view class="list" scroll-y>
			<view class="answer-sort">
				<a href="">默认排序 <i class="fa fa-chevron-down"></i></a>
			</view>
			<view v-for="i in 3" :key="i">
			<answer-card>谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~ 利益相关：
			谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~ 利益相关：
			谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~ 利益相关：
			谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~ 利益相关：
			谢邀。人在美国，刚下飞机。博士学位，月入千万。熟人太多，匿了匿了~ 利益相关：</answer-card>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import answerCard from '../../components/youzhi/answer-card.vue'
	import questionHead from '../../components/youzhi/question-head.vue'
	export default{
		components: {
			answerCard, questionHead
		},
	}
</script>

<style>
	.answer-sort{
		color: #9A9A9A;
		margin: 16upx;
		text-align: right;
		font-size: 28upx;
	}
</style>
