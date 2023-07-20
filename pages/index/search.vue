<template>
	<view class="container">
		<view class="inp">
			<image src="../../static/icon/back.png" mode="" @click="back"></image>
			<input type="text" placeholder="请输入关键字">
			<image src="../../static/icon/sousuo.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				});
			}
		}
	}
</script>

<style lang="less">
	.container {
		.inp {
			margin: 20rpx;
			position: relative;

			image:first-child {
				position: absolute;
				width: 40rpx;
				height: 40rpx;
				top: 10rpx;
				left: 10rpx;
				z-index: 10;
			}

			image:last-child {
				position: absolute;
				width: 40rpx;
				height: 40rpx;
				top: 10rpx;
				right: 20rpx;
			}

			input {
				background-color: #e2e2e2;
				height: 60rpx;
				font-size: 26rpx;
				text-indent: 60rpx;
				border-radius: 30rpx;
			}
		}
	}
</style>