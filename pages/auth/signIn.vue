<template>
	<view class="container">
		<view class="yz-signin-input">
			<h5 class="capital">使用账号密码登录</h5>
			<input v-model="email" class="yz-input" name="username" placeholder="账号" />
			<input v-model="password" type="password" class="yz-input" name="password" placeholder="密码" />
		</view>
		<view>
			<button class="yz-button primary" @click="signIn()" :disabled="disableSignIn">登录</button>
		</view>
		<view class="yz-buttom">
			<p>其他登录方式</p>
			<button class="yz-button primary">微信登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				email:undefined,
				phoneNum:undefined,
				password:undefined,
				disableSignIn:true,
			}
		},
		watch:{
			email: function(val){
				this.disableSignIn = !(val && this.password);
			},
			password: function(val){
				this.disableSignIn = !(val && this.email);
			},
		},
		methods: {
			signIn(){
				uni.request({
					url:"/signin",
					method:"POST",
					data:{
						email:this.email,
						password:this.password
					},
					success:(result) => {
						console.log(123)
					}
				})
			}
		},
		onLoad() {

		}
	}
</script>

<style>
	.capital{
		text-align: center;
		color: rgba(0,0,0,0.7);
	}
	.yz-buttom{
		vertical-align: buttom;
	}
</style>
