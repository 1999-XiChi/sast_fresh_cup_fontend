<template>
	<view>
		<input v-model="code" class="yz-input text-center" name="username" placeholder="请输入发送到邮箱的六位验证码" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				code:undefined,
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
						},
						success:(result) => {
							// TODO
						}
					});
				}
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
