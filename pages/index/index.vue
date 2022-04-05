<template>
	<view >
		<view class="top"></view>
			<swiper class="sw1" autoplay="true" duration="1000" circular="true" indicator-dots="true">
				<swiper-item  class="sw_item" v-for="(item,i) in sw_items" :key="i">
					<image class="sw_item_in" mode="scaleToFill" :src="item" @click="previewImg(i)"></image>
				</swiper-item>
			</swiper>
			<view class="gua">
				<image src="../../static/icons/fire_42.360153256705px_1226127_easyicon.net.png" class="ic"></image>
				<p class="HOT">单个页面游戏制作挑战赛正在火热进行！</p>
			</view>
		<scroll-view class="in1">
			<view class="it" v-for="(item,i) in list1" :key="i">
				<image mode="scaleToFill" class="ic1"></image>
				<h2 class="te1">{{item.name}}</h2>
				<p class="t2">{{item.type}}</p>
				<p class="t3">{{item.bing}}</p>
				<view class="down"><p>下载</p></view>
			</view>
			
		</scroll-view>
		<view class="bo"></view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				list1: null,
				sw_items:["https://i.loli.net/2021/02/19/pfXa4QnC8Y9KiSq.png"]
			}
		},
		onLoad() {
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
			    url: 'http://3697c2a501.imdo.co/data',
			    success: (res) => {
			        
					if(res.data.a !== "1.0.0"){
						uni.showToast({
							title:"检测到新版本",
							icon:"none"
						})
					};
			    }
			});
			uni.request({
			    url: 'http://3697c2a501.imdo.co/api/menu?index=2',
			    success: (res) => {
			        console.log(res.data); 
					that.list1 = res.data;
			    }
			});
		},
		methods: {
			previewImg(i) {
				var that = this
				uni.previewImage({
					current: that.sw_items[i],
					urls:that.sw_items,
					loop:true,
					indicator:'default'
				})
			}
		}
	}
</script>

<style>
		.top{
			height: var(--status-bar-height);
			width: 100%;
			background-color: #2ecc71;
		},
		.title{
			text-align: center;
			font-size: 50rpx;
		}
		.sw1{
			height: 400rpx;
			width: 100%;
		}
		.sw_item_in{
			height: 400rpx;
			width: 100%;
		}
		.gua{
			height: 80rpx;
			width: 100%;
			background-color: rgb(226, 226, 226);
		}
		.gua image{
			display: inline-block;
			float: left;
			margin-top: 10rpx;
		}
		.HOT{
			display: inline-block;
			float: left;
			margin-top: 15rpx;
		}
		text{
			display: block;
		}
		.ic{
			display: inline-block;
			height: 50rpx;
			width: 50rpx;
		}
		.in1{
			background-color: #C0C0C0;
			
		}
		.it{
			height: 150rpx;
			width: 100%;
			background-color: #FFFFFF;
			margin-bottom: 2rpx;
		}
		.ic1{
			float: left;
			height: 120rpx;
			width: 120rpx;
			margin-top: 15rpx;
			margin-left: 10rpx;
			background-color: #333333;
			border-radius: 15%;
		}
		.te1{
			float: left;
			margin-top: 15rpx;
			margin-left: 15rpx;
		}
		.t2{
			float: left;
			margin-left: -95rpx;
			margin-top: 80rpx;
			color: #007AFF;
		}
		.t3{
			float: left;
			margin-left: 10rpx;
			margin-top: 80rpx;
			color: #808080;
		}
		.down{
			float: right;
			height: 80rpx;
			width: 150rpx;
			margin-top: 35rpx;
			margin-right: 15rpx;
			border-radius: 15%;
			border: 1rpx solid #4CD964;
		}
		.down p{
			margin-top: 10rpx;
			text-align: center;
			font-size: 40rpx;
			color: #4CD964;
		}
</style>
