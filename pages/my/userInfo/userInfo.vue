<template>
	<view>
		<view class="head">
		  <view class="headProtrait">
		    <image v-bind:src="image" @tap="chooseImage"></image>
			<image src="../../../static/picture.png"></image>
		  </view>
		  <view class="headProtrait_title">头像</view>
		</view>
		<uni-list>
			<uni-list-item title="昵称" :note="userName" @click="Visible1 = true"/>
			      <prompt :visible.sync="Visible1" title="昵称" @confirm="userNameConfirm" />
			<uni-list-item title="学号" :note="studentId" @click="Visible2 = true"/>
			      <prompt :visible.sync="Visible2" title="学号" @confirm="studentIdConfirm" />
			<uni-list-item title="真实姓名" :note="trueName" @click="Visible3 = true"/>
			       <prompt :visible.sync="Visible3" title="真实姓名" @confirm="trueNameConfirm" />
			<picker @change="sexChange" :value="index" :range="sexes">
			        <uni-list-item title="性别" :note="sex"/>
			</picker> 
			<picker @change="gradeChange" :value="index" :range="grades">
			        <uni-list-item title="年级" :note="grade"/>
			</picker> 
			<picker mode="multiSelector" @change="majorChange" :value="majorIndex" :range="majors">
			       <uni-list-item title="专业" :note="majorNote"/>
			</picker> 	
		</uni-list>	
		<navigator url="/pages/my/myInfo" hover-class="navigator-hover">
			<button class="yz-button" type="primary">保存</button>
		</navigator>
		<navigator url="/pages/auth/signIn" hover-class="navigator-hover">
			<button class="yz-button" type="warn">退出登录</button>
		</navigator>
	</view>
</template>

<script>
	import uniList from '@/components/uni-list/uni-list.vue'
	import uniListItem from '@/components/uni-list-item/uni-list-item.vue'
	import Prompt from '@/components/zz-prompt/index.vue'
	export default {
		components:{
			uniList, uniListItem,Prompt
		},
		data() {
			return {
				Visible1: false,
				Visible2: false,
				Visible3: false,
				index: 0,
				majorIndex: [0,0],
				userName: '未登录',
				studentId: '-',
				grade:'2019',
				trueName: '',
				sex:'男',
				major: ['计算机软件工程网络空间安全学院','计算机科学与技术'],
				majorNote: '计算机科学与技术',          //uni-list-item的note属性不可以以数组形式显示更新
				image:'../../../static/headProtrait.jpeg',
				grades:['2019','2018','2017','2016'],
				sexes:['男','女'],
				majors:[['计算机软件工程网络空间安全学院','微电子'],['计算机科学与技术','软件工程','网络空间安全']],
			}
		},
		methods: {
			chooseImage: async function() {
					uni.chooseImage({
						count:1,
						sourceType: ['album'],
						success: (res) => {
							this.image = res.tempFilePaths[0]
						}
					})
				},
			gradeChange: function(e) {
                this.index = e.target.value
				this.grade = this.grades[this.index]
            },	
			sexChange: function(e) {
			    this.index = e.target.value
				this.sex = this.sexes[this.index]
			},	
			majorChange: function(e) {
			    this.majorIndex[0] = e.target.value[0]
				this.majorIndex[1] = e.target.value[1]
			    this.major[0] = this.majors[0][this.majorIndex[0]]
				this.major[1] = this.majors[1][this.majorIndex[1]]
				this.majorNote = this.major[1]
			},	
			function (){
				//uni自带的picker不支持二级联动，major的picker需要自行写代码，
			},
			userNameConfirm(val) {
               this.userName = val;
            },
			studentIdConfirm(val) {
			   this.studentId = val;
			},
			trueNameConfirm(val) {
			   this.trueName = val;
			},
		}
	}
</script>

<style scoped>
	.head{
		overflow: hidden;
	}
	.headProtrait{
		width:210upx;
		height:210upx;
		border-radius:50%;
		border: 2upx solid #BAC1C2;
		float:left;
		margin:10upx;
		position:relative;
	}
    .headProtrait image:nth-child(1){
	   height: 200upx;
	   width: 200upx;
	   border-radius:50%;
	   display:block;
	   margin:5upx;
    }
	.headProtrait image:nth-child(2){
	  display:none;
	}
	.headProtrait:hover image:nth-child(1){
		opacity: 0.8;
	}
	.headProtrait:hover  image:nth-child(2){
	  height: 50upx;
	  width: 50upx;
	  display:block;
	  position:absolute;
	  top:80upx;
	  left:80upx;
	  opacity: 0.8;
	}
	.headProtrait_title{
		margin-top:150upx;
	}
</style>
