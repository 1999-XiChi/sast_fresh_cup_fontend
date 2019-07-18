<template>
	<view class="container">
		<view class="yz-signin-input">
			<h5 class="capital">注册</h5>
			<input class="yz-input" name="username" placeholder="邮箱" />
			<input type="password" class="yz-input" name="password" placeholder="密码" />
			<input type="password" class="yz-input" name="password" placeholder="确认密码" />
		</view>
		<view>
			<button class="yz-button primary" formType="submit" disabled>登录</button>
		</view>
		<view class="yz-buttom">
			<p>其他登录方式</p>
			<button class="yz-button primary" formType="submit">微信登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			signIn(){
				
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
