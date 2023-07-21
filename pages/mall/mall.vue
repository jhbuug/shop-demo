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
		<!-- 商品 -->
		<view class="goods">
			<view class="item" v-for="(item,index) in data.list8" :key="index" @click="toDetail(item)">
				<image :src="item.imgUrls[0]" mode=""></image>
				<text class="title"><img src="../../static/icon/tianmao.png" alt="">{{item.title}}</text>
				<view class="LR">
					<text class="price">￥{{item.price}}.00</text><text class="xL">{{item.xiaoLiang}}人付款</text>
				</view>
				<view class="text">
					<text>{{item.text1}}</text>
					<text>{{item.text2}}</text>
				</view>
				<text class="shopName">{{item.shopName}}</text>
			</view>
		</view>
		<!-- 商品 -->
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
			toDetail(item) {
				console.log(item)
				uni.navigateTo({
					url: '/pages/mall/detail?info=' + encodeURIComponent(JSON.stringify(item))
				})
			}
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

		.goods {
			display: flex;
			justify-content: center;
			flex-wrap: wrap;

			.item {
				width: 45%;
				margin: 20rpx 10rpx;

				.shopName {
					font-size: 30rpx;
					padding-top: 5rpx;
				}

				.text {
					display: flex;
					padding: 5rpx 0;

					text {
						font-size: 26rpx;
						border: 1px solid #e45304;
						border-radius: 3px;
						text-align: center;
						box-sizing: border-box;
						padding: 4rpx;
					}

					text:first-child {
						margin-right: 20rpx;
					}
				}

				text {
					display: block;

					img {
						height: 28rpx;
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
					padding: 5rpx 0;
				}

				.LR {
					display: flex;
					justify-content: space-between;
					align-items: center;
					padding: 5rpx 0;
					color: #e45304;
					font-weight: 700;

					text:last-child {
						font-size: 26rpx;
						color: #aaa;
					}
				}

				image {
					width: 100%;
					border-radius: 12px;
				}
			}
		}
	}
</style>