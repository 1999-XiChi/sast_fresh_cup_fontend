<template>
	<view>
		<input v-model="code" class="yz-input text-center" name="username" placeholder="请输入发送到邮箱的六位验证码" />
		<p class="text-center">{{content}}</p>
		<button v-show="resend" @click="sendCode()" class="text-center">重新发送验证码</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				email:undefined,
				code:undefined,
				content:"",
				clock:60,
				resend:false,
			}
		},
		watch:{
			code: function(val){
				if(val.toString().length === 6){
					uni.request({
						url:"",
						method:"POST",
						data:{
							code:this.code
						}
					}).then(result => {
						if(result.data.success){
							
						}else{
							this.content = "验证码不正确";
						}
						
					})
				}
			}
		},
		methods: {
			countDown() {
				this.resend = false;
				let timeout = setInterval(() => {
				    this.clock--;
					if (this.clock === 0){
						clearInterval(timeout);
						this.resend = true;
					}
				    this.content = `接收验证码可能需要 ${this.clock}  秒`
				},1000);
			},
			sendCode(){
				uni.request({
					url:"http://106.14.214.188:3000/mock/11/sendcaptcha",
					method:"POST",
					data:{
						email:this.email
					},
					success:(result) => {
						this.countDown();
					}
				})
			}
		},
		onLoad(email){
			this.email = email.email; //这里包装了一层email，记得取出
			this.sendCode();
		}
	}
</script>

<style>

</style>
