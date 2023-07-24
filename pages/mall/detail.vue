<template>
	<view class="container">
		<u-icon class="back" name="arrow-left" color="#fff" size="28" @click="back"></u-icon>
		<!-- 轮播图 -->
		<view class="banner">
			<u-swiper :list="info.imgUrls" @change="e => currentNum = e.current" :autoplay="false" height="100%"
				indicatorStyle="right: 20px">
				<view slot="indicator" class="indicator-num">
					<text class="indicator-num__text">{{ currentNum + 1 }}/{{ info.imgUrls.length }}</text>
				</view>
			</u-swiper>
		</view>
		<!-- 轮播图 -->
		<!-- 主体内容 -->
		<view class="main">
			<view class="detail">
				<view class="price">
					<view>￥{{info.price}}起</view>
					<view>新品促销券后￥<text>{{info.price - 100}}</text> 起</view>
				</view>
				<view class="title">
					<img src="../../static/icon/tianmao.png" alt="">{{info.title}}
				</view>
				<view class="xL">
					月销 {{ info.xiaoLiang}}
				</view>
			</view>
		</view>
		<!-- 主体内容 -->
		<!-- 底部导航栏 -->
		<view class="goods-carts">
			<uni-goods-nav :options="data.options" :fill="true" :button-group="data.buttonGroup" @click="onClick"
				@buttonClick="buttonClick" />
		</view>
		<!-- 底部导航栏 -->
	</view>
</template>

<script>
	import JsonData from "../../data/index.json"
	export default {
		components: {},
		data() {
			return {
				data: JsonData,
				info: {},
				cartinfo: JsonData.options[2].info,
				currentNum: 0
			}
		},
		onLoad(options) {
			let info = JSON.parse(decodeURIComponent(options.info))
			console.log(info)
			this.info = info
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				});
			},
			onClick(e) {
				console.log(e)
				if (e.index == 2) {
					uni.switchTab({
						url: '/pages/shoppingTrolley/shoppingTrolley'
					})
				}
			},
			buttonClick(e) {
				if (e.index) { //立即购买

				} else { //加入购物车
					console.log(e)
					this.cartinfo++
					JsonData.options[2].info = this.cartinfo;
					console.log(JsonData.options[2].info)
				}

			}
		}
	}
</script>

<style lang="scss">
	.container {
		padding-bottom: 100rpx;
	}

	.banner {
		height: 550px;
	}

	.main {
		margin: 0 20rpx;

		.price {
			display: flex;
			padding: 20rpx 5rpx;
			align-items: center;
			font-weight: 700;
			font-size: 35rpx;

			view:first-child {
				margin-right: 20rpx;
				color: #e93423;
			}

			view:last-child {
				background-color: #e93423;
				border-radius: 50rpx;
				padding: 5rpx 15rpx;
				font-size: 20rpx;
				color: white;
				display: flex;
				align-items: center;

				text {
					font-size: 30rpx;
				}
			}
		}

		.title {
			overflow: hidden;
			-webkit-line-clamp: 2;
			text-overflow: ellipsis;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			font-size: 30rpx;
			font-weight: 700;
			padding: 0 5rpx;

			img {
				height: 28rpx;
			}
		}

		.xL {
			font-size: 26rpx;
			padding: 10rpx 5rpx;
		}
	}

	.back {
		position: fixed;
		left: 10rpx;
		top: 10rpx;
		z-index: 10;
		background-color: #000;
		border-radius: 50%;
		padding: 5rpx;
		opacity: 0.4
	}

	.indicator {
		@include flex(row);
		justify-content: center;

		&__dot {
			height: 6px;
			width: 6px;
			border-radius: 100px;
			background-color: rgba(255, 255, 255, 0.35);
			margin: 0 5px;
			transition: background-color 0.3s;

			&--active {
				background-color: #ffffff;
			}
		}
	}

	.indicator-num {
		padding: 2px 0;
		background-color: rgba(0, 0, 0, 0.35);
		border-radius: 100px;
		width: 35px;
		@include flex;
		justify-content: center;

		&__text {
			color: #FFFFFF;
			font-size: 12px;
		}
	}

	.goods-carts {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		position: fixed;
		left: 0;
		right: 0;
		/* #ifdef H5 */
		left: var(--window-left);
		right: var(--window-right);
		/* #endif */
		bottom: 0;
	}
</style>