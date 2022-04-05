<template>
	<view>
		<view class="top"></view>
		<view class="t1">
			<view @click="back()"> <返回 </view>
		</view>
		<h1 class="title">{{info.name}}</h1>
		<image mode="scaleToFill" :src="info.img" class="image"></image>
		<p>{{info.text}}</p>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info:null
			}
		},
		onLoad(thing){
			var that = this;
			uni.request({
			    url: 'http://3697c2a501.imdo.co',
			    success: (res) => {
			        //console.log(res.data); 
			    },
				fail() {
					uni.showToast({
						title:"连接服务器超时",
						icon:"none"
					})
				}
			});
			uni.request({
			    url: 'http://3697c2a501.imdo.co/comp?id='+thing.key,
			    success: (res) => {
			        console.log(res.data); 
					that.info = res.data[0];
			    }
			});
		},
		methods: {
			back() {
				uni.navigateBack()
			}
		}
	}
</script>

<style>
	.top{
		height: var(--status-bar-height);
		width: 100%;
		background-color: #2ecc71;
	}
	.t1{
		position: relative;
		height: 100rpx;
		width: 100%;
		background-color: #2ecc71;
	}
	.t1 view{
		position: absolute;
		font-size: 50rpx;
		height: 80rpx;
		top: 15rpx;
		left: 15rpx;
	}
	.title{
		text-align: center;
	}
	.image{
		height: 500rpx;
		width: 100%;
	}
</style>
