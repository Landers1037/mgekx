<template>
	<view>
		<web-view :src="src" v-if="src.length>0"></web-view>
		<text v-else class="error" @click="back">出现错误💊</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: ""
			}
		},
		onLoad(option) {
			if(option.src){
				let src = option.src;
				this.src = "http://" + src;
			}
		},
		methods: {
			back(){
				uni.navigateBack({
					delta:2
				})
			}
		},
		onPullDownRefresh(){
			uni.reload();
			setTimeout(function () {
				uni.stopPullDownRefresh();
				}, 1000);
		},
	}
</script>

<style>
	.error{
		text-align: center;
		display: block;
		margin-top: 150rpx;
		color: #606060;
		font-size: 18px;
	}
</style>
