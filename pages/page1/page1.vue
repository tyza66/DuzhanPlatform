<template >
	<view class="cc">
		<view class="top"></view>
		<view class="need"><view class="tit1">近期比赛</view><p @click="kai">办比赛</p></view>
		<scroll-view class="bac" >
			<view class="ina" v-for="(item,i) in lists" :key="i" @click="goin(item.id)">
				<view class="left">
					<image :src="lists[0].img"></image>
				</view>
				<view class="right">
					<h3>{{item.name}}</h3>
					<p>{{item.text}}</p>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				lists:null
			}
		},
		onShow() {
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
			    url: 'http://3697c2a501.imdo.co/api/menu?index=1',
			    success: (res) => {
			        //console.log(res.data); 
					that.lists = res.data;
			    }
			});
		},
		methods: {
			goin(it) {
				uni.navigateTo({
					url:"../page4/page4?key="+it.toString()
				})
			},
			kai() {
				uni.navigateTo({
					url:"../page5/page5"
				})
			}
		}
	}
</script>

<style>
	.top{
		height: var(--status-bar-height);
		width: 100%;
		background-color: #4CD964;
	},
	.bac{
		background-color: #C8C7CC;
	}
	.ina{
		display: block;
		height: 300rpx;
		width: 100%;
		background-color: #ecf0f1;
		margin-bottom: 2rpx;
	}
	.left{
		display:inline-block;
		float: left;
		height:250rpx;
		width: 300rpx;
		margin-top: 25rpx;
		margin-left: 5rpx;
	}
	.left image{
		height: 100%;
		width: 100%;
	}
	.right{
		display:inline-block;
		float: left;
		height:250rpx;
		width: 440rpx;
		margin-top: 30rpx;
		margin-left: 5rpx;
	}
	.need{
		height: 80rpx;
		background-color: #4CD964;
	}
	.tit1{
		display: flex; 
		flex-direction: row; 
		justify-content: center;
		font-size: 50rpx;
	}
	.need p{
		float: right;
		margin-top: -50rpx;
	}
	.right p{
		max-width: 440px;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: inherit;
	}
</style>
