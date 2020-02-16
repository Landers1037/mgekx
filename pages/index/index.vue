<template>
	<view class="content">
		<image class="logo" src="/static/mgek.png"></image>
		<template>
			<uni-drawer :visible="draw" @close="redraw">
				<view>
						<view class="top-d">
							<image src="../../static/mgek.png" class="drawer-img"></image>
							<text style="font-size: 16px;color: #606060;padding: 10px;">MgekX & Landers</text>
						</view>
						
						<view class="title-d" @click="home">
							<uni-icons type="smallcircle" size="20" color="#808080" class="icon"></uni-icons>
							主页
						</view>
						<p class="hr"></p>
						<view class="title-d" @click="blog">
							<uni-icons type="star-filled" size="20" color="#808080" class="icon"></uni-icons>
							博客
						</view>
						<view class="title-d" @click="mgek">
							<uni-icons type="shop" size="20" color="#808080" class="icon"></uni-icons>
							Mgek项目
						</view>
						<view class="title-d" @click="doc">
							<uni-icons type="paperclip" size="20" color="#808080" class="icon"></uni-icons>
							Mgek文档
						</view>
						<view class="title-d" @click="cloud">
							<uni-icons type="cloud-download" size="20" color="#808080" class="icon"></uni-icons>
							Mgek云
						</view>
						<p class="hr"></p>
						<view class="title-d" @click="rocket">
							<uni-icons type="paperplane" size="20" color="#808080" class="icon"></uni-icons>
							小火箭
						</view>
						<view class="title-d" @click="log">
							<uni-icons type="trash" size="20" color="#808080" class="icon"></uni-icons>
							日志
						</view>
						<view class="title-d" @click="about">
							<uni-icons type="heart-filled" size="20" color="#808080" class="icon"></uni-icons>
							关于
						</view>
						<view class="title-d" @click="email">
							<uni-icons type="email" size="20" color="#808080" class="icon"></uni-icons>
							订阅
						</view>						
				    </view>
				</uni-drawer>
		</template>
		    
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="mbody">
			<div class="article" @click="article">
				<text>New article</text>
			</div>
			<div class="blog" @click="blog">
				<text>Blog</text>
			</div>
			<div class="mgek" @click="mgek">
				<text>Mgek.cc</text>
			</div>
			<div class="doc" @click="doc">
				<text>Docs.</text>
			</div>
			<div class="cloud" @click="cloud">
				<text>Mgek Cloud</text>
			</div>
			<div class="github" @click="github">
				<text>GitHub</text>
			</div>
		</view>
	</view>
</template>

<script>
	import uniDrawer from '@/components/uni-drawer/uni-drawer.vue';
	import uniIcons from "@/components/uni-icons/uni-icons.vue";
	export default {
		data() {
			return {
				title: 'Landers1037',
				draw: false
			}
		},
		components:{uniDrawer,uniIcons},
		watch:{
			draw: function(){
				console.log(this.draw)
			}
		},
		onLoad() {

		},
		onNavigationBarButtonTap(e){
			this.draw = true;
		},
		methods: {
			redraw(){
				this.draw = false;
			},
			home(){
				uni.redirectTo({
					url:"../index/index",
					animationType: "slide-in-right",
					animationDuration: 400 
				})
			},
			article(){
				uni.navigateTo({
					url:'../web?src=lrenj.top/blog/newest',
					animationType: "slide-in-left",
					animationDuration: 300,
				});
			},
			blog(){
				uni.navigateTo({
					url:'../web?src=lrenj.top/blog/',
					animationType: "slide-in-left",
					animationDuration: 300,
				});
			},
			mgek(){
				uni.navigateTo({
					url:'../web?src=mgek.cc/mobile',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},
			doc(){
				uni.navigateTo({
					url:'../web?src=doc.mgek.cc/docs/',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},
			cloud(){
				uni.navigateTo({
					url:'../cloud',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},	
			github(){
				uni.navigateTo({
					url:'../web?src=github.com/landers1037',
					animationType: "slide-in-left",
					animationDuration: 300
				})
			},	
			log(){
				uni.navigateTo({
					url:'../log',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},	
			about(){
				uni.navigateTo({
					url:'../about',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},	
			email(){
				uni.navigateTo({
					url:'../email',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},			
			rocket(){
				uni.navigateTo({
					url:'../ssr',
					animationType: "slide-in-left",
					animationDuration: 300
				});
			},														
		},
		onPullDownRefresh(){
			setTimeout(function () {
				uni.stopPullDownRefresh();
				}, 1000);
		},
		
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 240rpx;
		width: 240rpx;
		margin-top: 30rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 30rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.mbody{
		padding: 10rpx;
		margin-top: 50rpx;
		font-weight: bold;
	}
	.mbody .article{
		background-color: #378de5;
		width: 440rpx;
		color: #FFFFFF;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}
	.mbody .blog{
		background-color: #495a80;
		width: 440rpx;
		color: #FFFFFF;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}	
	.mbody .mgek{
		background-color: #FF9700;
		width: 440rpx;
		color: #404040;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}
	.mbody .doc{
		background-color: #465158;
		width: 440rpx;
		color: #C0C0C0;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}	
	.mbody .cloud{
		background-color: #00755e;
		width: 440rpx;
		color: #F5F5F5;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}		
	.mbody .github{
		background-color: #222222;
		width: 440rpx;
		color: #F5F5F5;
		padding: 25rpx 30rpx;
		border-radius: 5px;
		margin-top: 15rpx;
		margin-bottom: 15rpx;
	}	
	/deep/ .uni-drawer__content { width: 400rpx; } 
	.top-d{
		background-color: #f0f0f0;
		padding: 40rpx 15rpx;
		margin-bottom: 40rpx;
	}
	.drawer-img{
		width: 150rpx;
		height: 150rpx;
		display: block;
	}
	.hr{
		border: none;
		height: 0;
		border-bottom: 1px solid #F0F0F0;
		padding: 4rpx 0;
	}
	.title-d{
		padding: 20rpx 25rpx;
		font-size: 17px;
		font-weight: bold;
	}
	.title-d:hover{
		background-color: #f0f0f0;
	}
	.icon{
		padding: 0 40rpx 0 20rpx;
	}
</style>
