<template>
	<view class="container">
		<!-- 头部内容 -->
		<view class="header">
			<view class="up">
				<view class="left">
					<image src="" mode=""></image>
					<view class="text">
						<text>182****5487</text>
						<view class="id">
							<view><text>ID: 9527<img src="" alt=""></text></view>
							<u-icon name="edit-pen" color="#fff" size="16"></u-icon>
						</view>
					</view>
				</view>
				<view class="right">
					<view><u-icon name="setting" color="#fff" size="20" top="6rpx"></u-icon></view>
					<view><u-icon name="chat" color="#fff" size="24"></u-icon></view>
				</view>
			</view>
			<view class="down">
				<view class="item">
					<text>114514</text>
					<text>额度</text>
				</view>
				<view class="item">
					<text>9527</text>
					<text>优惠券</text>
				</view>
				<view class="item">
					<text>999</text>
					<text>浏览记录</text>
				</view>
			</view>
		</view>
		<!-- 头部内容 -->
		<!-- 主体内容 -->
		<view class="main">
			<view class="order">
				<view class="up">
					<view class="item">我的订单</view>
					<view class="item">
						<view>全部订单</view><u-icon name="arrow-right" color="#000" size="20" top="2rpx"></u-icon>
					</view>
				</view>
				<view class="down">
					<view class="item">
						<image src="../../static/icon/daizhifu.png" mode=""></image>
						<text>待付款</text>
					</view>
					<view class="item">
						<image src="../../static/icon/daifahuo.png" mode=""></image>
						<text>待发货</text>
					</view>
					<view class="item">
						<image src="../../static/icon/daishouhuo.png" mode=""></image>
						<text>待收货</text>
					</view>
					<view class="item">
						<image src="../../static/icon/wodexiaoxi.png" mode=""></image>
						<text>待评价</text>
					</view>
					<view class="item">
						<image src="../../static/icon/shouhoutuikuan.png" mode=""></image>
						<text>售后/退款</text>
					</view>
				</view>
			</view>
			<view class="my">
				<view class="up">
					<view class="item">我的服务</view>
				</view>
				<view class="down">
					<view class="item">
						<image src="../../static/icon/wenti.png" mode="" style="background-color: #558cff;"></image>
						<text>问题反馈</text>
					</view>
					<view class="item">
						<image src="../../static/icon/iconfontshangjia.png" mode="" style="background-color: #fba224;">
						</image>
						<text>商家入住</text>
					</view>
					<view class="item">
						<image src="../../static/icon/daohangdizhi.png" mode="" style="background-color: #f5671f;">
						</image>
						<text>地址管理</text>
					</view>
					<view class="item">
						<image src="../../static/icon/xiai.png" mode="" style="background-color: #8480f8;">
						</image>
						<text>用户收藏</text>
					</view>
				</view>
			</view>
			<view class="keFu">
				<text>点我联系客服</text>
				<text>上班时间：10:00 - 19:00</text>
			</view>
		</view>
		<!-- 主体内容 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="less">
	.container {
		// background-color: #e93423;
		background: linear-gradient(to bottom, #e93423 0, #e93423 400rpx, #f0f0f0 400rpx, #f0f0f0 100%);
		height: 100%;
		width: 100%;
		position: absolute;

		.header {
			margin-top: 123rpx;
			color: white;

			.up {
				display: flex;
				justify-content: space-between;
				margin: 0 27rpx;

				.left {
					display: flex;
					align-items: center;

					.text {
						margin-left: 20rpx;

						.id {
							display: flex;
							opacity: 0.8;
							font-size: 26rpx;

							view {
								margin: 0 20rpx 0 5rpx;
							}
						}
					}

					image {
						height: 120rpx;
						width: 120rpx;
						background-color: aliceblue;
						border-radius: 50%;
					}
				}

				.right {
					display: flex;

					view:first-child {
						margin-right: 20rpx;
					}
				}
			}

			.down {
				display: flex;
				justify-content: center;
				text-align: center;
				padding: 15rpx;

				.item {
					padding: 0 25rpx;
					border-right: 1px solid white;

					text {
						display: block;
					}

					text:last-child {
						font-size: 24rpx;
						opacity: 0.8;
					}
				}

				.item:last-child {
					border-right: none;
				}

			}
		}

		.main {
			.order {
				background-color: #ffffff;
				margin: 0 20rpx;
				padding: 10rpx 25rpx;
				border-radius: 12px;

				.up {
					display: flex;
					justify-content: space-between;

					.item:last-child {
						display: flex;
					}
				}

				.down {
					display: flex;
					justify-content: space-between;
					padding: 20rpx 10rpx;

					.item {
						text-align: center;

						text {
							display: block;
							font-size: 28rpx;
						}

						image {
							width: 60rpx;
							height: 60rpx;
						}
					}
				}
			}

			.my {
				background-color: #ffffff;
				margin: 20rpx 20rpx;
				padding: 10rpx 25rpx;
				border-radius: 12px;

				.up {
					font-weight: 700;
				}

				.down {
					display: flex;
					justify-content: space-between;
					padding: 20rpx 10rpx;

					.item {
						text-align: center;

						text {
							display: block;
							font-size: 28rpx;
						}

						image {
							width: 40rpx;
							height: 40rpx;
							border-radius: 50%;
							padding: 10rpx;
						}
					}
				}
			}

			.keFu {
				background: linear-gradient(to right, #fa3465, #f43a2d);
				margin: 0 20rpx;
				padding: 10rpx;
				border-radius: 50rpx;
				color: white;

				text {
					display: block;
					text-align: center;
					font-size: 28rpx;
					height: 40rpx;
				}
			}
		}
	}
</style>