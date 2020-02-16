<template>
	<view style="position: 20rpx;text-align: center;">
		 <image src="../static/ssr.jpg" class="ssri"></image>
		 <p style="font-size: 14px;color: #9f9f9f;">{{time}}</p>
		 <uni-list>
		     <uni-list-item title="🚀 查看地址" v-for="item in ssrlist" :key="item" :showArrow="false" @click="show(item)">
				 
			 </uni-list-item>
		 </uni-list>
		 <uni-fab
		             :pattern="pattern"
		             horizontal="right"
		             vertical="bottom"
		             direction="horizontal"
		             :popMenu="false"
					 @fabClick="safeupdate"
		         ></uni-fab>
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	import uniFab from '@/components/uni-fab/uni-fab.vue';
	export default {
		data() {
			return {
				ssrlist: {},
				time: '',
				pattern:{
					buttonColor: "#378de5"
				},
				count: 0,
				dcount: 20
			}
		},
		components: {uniList,uniListItem,uniFab},
		methods: {
			getssr()
			{
				uni.request({
					url: "http://api.mgek.cc/ssr",
					sslVerify: false,
					success:(res)=> {
						this.ssrlist = res.data["list"];
						this.time = res.data["updatetime"]
					},
					fail: (err) => {
						uni.showModal({
							content:'获取数据失败'
						});
					}
				})
			},
			show(item){
				uni.showModal({
					title: "已复制到剪贴板",
					content: item,
					complete() {
						uni.setClipboardData({
							data: item,
						})
					}
				});
			},
			update(){
				uni.request({
					url:"http://api.mgek.cc/ssr?up=yes",
					method:'POST',
					success: (res) => {
						uni.showModal({
							content:"列表更新完成"
						});
					},
					fail() {
						uni.showModal({
							content:"列表更新失败"
						});
					}
				});
			},
			safeupdate(){
				let c = this.count;
				if(c<4){
					this.update()
					this.count++;
				}else{
					if(this.dcount<2){
						this.count = 0;
					}else{
						this.dcount--;
						uni.showModal({
							content:"你请求的过快"
						});
					} 
				}
			}
		},
		onLoad() {
			this.getssr()
		},
		onPullDownRefresh(){
			this.getssr();
			setTimeout(function () {
				uni.stopPullDownRefresh();
				}, 1000);
		},
	}
</script>

<style>
	.ssri{
		width: 250rpx;
		height: 250rpx;
		border-radius: 50%;
		margin: 40rpx 0 60rpx 0;
	}
</style>
