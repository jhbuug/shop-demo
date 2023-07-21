<template>
	<view class="container">
		<!-- 头部内容 -->
		<view class="header">
			<view class="up">
				<view class="select">
					<view class="item">商城</view>
					<view class="item">商户门店</view>
				</view>
				<view class="inp">
					<img src="../../static/icon/sousuo.png" alt="">
					<input type="text" placeholder="搜索商品" @click="toSearch">
				</view>
				<image src="../../static/icon/xiazai16.png" mode=""></image>
			</view>
			<!-- tags -->
			<u-tabs :list="data.list6" lineColor="white"
				:activeStyle="{color: 'white',fontWeight: '700',fontSize:'30rpx'}"
				:inactiveStyle="{color: 'white',fontSize:'28rpx'}" itemStyle="padding:20rpx 12rpx">
				<view slot="right" style="padding-left: 4rpx;" @tap="$u.toast('插槽被点击')">
					<u-icon name="list" color="#fff" size="21" bold></u-icon>
				</view>
			</u-tabs>
			<!-- tags -->
		</view>
		<!-- 头部内容 -->
		<!-- 主体内容 -->
		<!-- 轮播图 -->
		<view class="banner">
			<u-swiper :list="data.list7" bgColor="transparent" radius="12" height="100%"></u-swiper>
		</view>
		<!-- 轮播图 -->
		<!-- 主体内容 -->
	</view>
</template>

<script>
	import JsonData from "../../data/index.json"
	export default {
		data() {
			return {
				data: JsonData,
			};
		},
		methods: {
			toSearch() {
				uni.navigateTo({
					url: "/pages/index/search"
				})
			},
		}
	}
</script>

<style lang="less">
	.container {
		.header {
			background-color: #e93423;
			padding: 100rpx 10rpx 5rpx;

			.up {
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 0 20rpx;
			}

			.select {
				display: flex;
				width: 270rpx;
				font-size: 28rpx;

				:first-child {
					color: #e93423;
					font-weight: 700;
					border-radius: 50rpx;
					background-color: #fff;
					padding: 10rpx 40rpx;
				}

				:last-child {
					padding: 10rpx 10rpx;
					color: #fff
				}
			}

			.inp {
				margin: 0 20rpx;
				position: relative;
				flex-grow: 1;

				img {
					position: absolute;
					width: 40rpx;
					height: 40rpx;
					top: 10rpx;
					left: 10rpx;
				}

				input {
					background-color: white;
					height: 60rpx;
					font-size: 26rpx;
					text-indent: 60rpx;
					border-radius: 30rpx;
				}
			}

			image {
				width: 40rpx;
				height: 40rpx;
			}
		}

		.banner {
			width: 92%;
			height: 250rpx;
			margin: 20rpx auto;
			border-radius: 12px;
			overflow: hidden;
		}
	}
</style>