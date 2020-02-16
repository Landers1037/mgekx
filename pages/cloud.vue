<template>
	<view>
		<text style="text-align: center;display: block;padding: 20rpx;font-size: 20px;">云端备份资源</text>
		<uni-list>
		    <uni-list-item :title="item" v-for="item in list" :key="item"></uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	export default {
		data() {
			return {
				list: []
			}
		},
		watch:{
			list:function(){}
		},
		onLoad() {
			uni.request({
				url:"http://api.mgek.cc/mgek/cloudlist",
				sslVerify: false,
				header:{
					"checkme": "mgekx",
				},
				success:(res)=>{
					this.list = res.data;
				},
				fail:(err)=> {
					uni.showModal({
						content:'获取数据失败'
					});
				}
			});
		},
		methods: {
			
		},
		components: {uniList,uniListItem},
		onPullDownRefresh(){
			uni.request({
				url:"http://api.mgek.cc/mgek/cloudlist",
				sslVerify: false,
				header:{
					"checkme": "mgekx",
				},
				success:(res)=>{
					this.list = res.data;
				},
				fail:(err)=> {
					uni.showModal({
						content:'获取数据失败'
					});
				}
			});
			setTimeout(function () {
				uni.stopPullDownRefresh();
				}, 1000);
		},
	}
</script>

<style>

</style>
