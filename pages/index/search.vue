<template>
	<view class="container">
		<view class="inp">
			<image src="../../static/icon/back.png" mode="" @click="back"></image>
			<input type="text" placeholder="请输入关键字" v-model="keyword" @input="search">
			<image src="../../static/icon/sousuo.png" mode=""></image>
		</view>
		<!-- 搜索内容 -->
		<view class="goods">
			<view class="item" v-for="(item,index) in searchResult" :key="index" @click="toDetail(item)">
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
		<!-- 搜索内容 -->
		<!-- 商品 -->
		<view class="goods" v-if="!searchResult.length">
			<view class="item" v-for="(item,index) in info" :key="index" @click="toDetail(item)">
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
	</view>
</template>

<script>
	import JsonData from "../../data/index.json"
	export default {
		data() {
			return {
				info: JsonData.list8,
				keyword: "",
				searchResult: []
			};
		},
		methods: {
			back() {
				uni.navigateBack({
					delta: 1
				});
			},
			search() {
				// 根据关键字从数据源中筛选出相关的结果
				this.searchResult = this.info.filter(item => {
					return item.title.includes(this.keyword);
				});
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

		.goods {
			display: flex;
			// justify-content: space-between;
			flex-wrap: wrap;

			.item {
				width: 45%;
				margin: 20rpx 2.5%;

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