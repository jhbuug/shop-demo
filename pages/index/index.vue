<template>
	<view class="header">
		<view class="ztl">状态栏</view>
		<view class="inp">
			<input type="text" placeholder="请输入关键字">
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {}
		},
		methods: {

		}
	}
</script>

<style lang="less">
	.header {
		height: 350rpx;
		background-color: #0252ff;
		border-radius: 0 0 50px 50px;

		.ztl {
			height: 45rpx;
			line-height: 45rpx;
			// background-color: white;
			color: white;
			text-align: center;
		}
		.inp{
			padding: 20rpx 20rpx;
			input{
				background-color: white;
				height: 60rpx;
				text-indent: 60rpx;
				border-radius: 30rpx;
			}
		}
	}
</style>