<template>
	<view>
		<view class="top"></view>
		<view class="t1">
			<view @click="back()"> <返回 </view>
		</view>
		<h1 class="tit1">如何办比赛</h1>
		<text space="nbsp">{{text}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text:""
			}
		},
		onLoad(){
			
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
	.tit1{
		text-align: center;
	}
</style>
