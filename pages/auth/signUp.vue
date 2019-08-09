<template>
	<view class="container">
		<view class="yz-signin-input">
			<h5 class="capital">注册</h5>
			<input v-model="email" class="yz-input" name="username" placeholder="邮箱"/>
			<input v-model="password" type="password" class="yz-input" name="password" placeholder="密码"/>
			<input v-model="password_comfirm" type="password" class="yz-input" name="password" placeholder="确认密码" />
		</view>
		<view>
			<button class="yz-button primary" @click="signUp()" :disabled="disableSignUp">注册</button>
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
				password_comfirm:undefined,
				disableSignUp:true,
			}
		},
		watch:{
			email: function(val){
				this.disableSignUp = !(val && this.password && this.password_comfirm);
			},
			password: function(val){
				this.disableSignUp = !(val && this.email && this.password_comfirm);
			},
			password_comfirm: function(val){
				this.disableSignUp = !(val && this.email && this.password);
			}
		},
		methods: {
			signUp(){
				if (this.password !== this.password_comfirm){
					uni.showModal({
						title: "注册",
						content: "抱歉，两次输入的密码不一致。",
						showCancel: false,
						confirmText: "确定"
					});
					return;
				}
				uni.navigateTo({url: '/pages/auth/verifyemail?email=' + this.email });
				uni.request({
					url:"/register",
					method:"POST",
					data:{
						email:this.email,
						password:this.password
					},
					success:(result) => {

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

	.btn-primary{
		background-color: #528AF1;
		color: #fff;
	}
	.yz-buttom{
		top: calc();
		vertical-align: buttom;
	}
</style>
