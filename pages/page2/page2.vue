<template>
	<view>
		<view class="top"></view>
		<p class="zz">赞助我们</p>
		<text>{{tt}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tt:"多点点广告，求你了"
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.top{
		height: var(--status-bar-height);
		width: 100%;
		background-color: #F8F8F8;
	},
	.zz{
		font-size: 50rpx;
		text-align: center;
	}
</style>
