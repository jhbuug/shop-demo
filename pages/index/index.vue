<template>
	<view class="container">
		<!-- 头部 -->
		<view class="header">
			<!-- <view class="ztl">状态栏</view> -->
			<view class="inp">
				<img src="../../static/icon/sousuo.png" alt="">
				<input type="text" placeholder="请输入关键字" @click="toSearch">
			</view>
			<!-- 选项卡 -->
			<view class="tags">
				<u-tabs :list="data.list1" @click="headTagsClick" lineColor="white"
					:activeStyle="{color: 'white',fontWeight: '700',fontSize:'26rpx'}"
					:inactiveStyle="{color: 'white',fontSize:'24rpx'}" itemStyle="padding:15rpx 15rpx"></u-tabs>
			</view>
			<!-- 选项卡 -->
		</view>
		<!-- 头部 -->
		<!-- tags选项卡内容切换 -->
		<view class="headerTagsContent" v-show="onOffTags">
			<text>{{content}}</text>
		</view>
		<!-- tags选项卡内容切换 -->
		<!-- 轮播图 -->
		<view class="banner" v-show="onOffBanner">
			<u-swiper :list="data.list2" indicator indicatorMode="dot" indicatorStyle="dot" circular height="100%"
				bgColor="transparent" radius="12"></u-swiper>
		</view>
		<!-- 轮播图 -->
		<!-- 主体内容 -->
		<view class="main" v-show="onOffMain">
			<!-- 选项卡 -->
			<view class="tags">
				<u-tabs :list="data.list3" @click="mainTagsClick" lineColor="red"
					:activeStyle="{color: 'red',fontWeight: '700',fontSize:'26rpx'}"
					:inactiveStyle="{color: 'black',fontSize:'24rpx'}" itemStyle="padding:15rpx 15rpx"></u-tabs>
			</view>
			<!-- 选项卡 -->
			<!-- maintags选项卡内容切换 -->
			<view class="mainTagsContent" v-show="onOffMainTags">
				<text>{{mainContent}}</text>
			</view>
			<!-- maintags选项卡内容切换 -->
			<view class="maincontent" v-show="onOffMainContent">
				<!-- 15个图标 -->
				<view class="cars">
					<view class="item" v-for="(item,index) in data.list4" :key="index" @click="toDetail(item)">
						<img :src="item.img" alt="">
						<view>{{item.name}}</view>
					</view>
				</view>
				<!-- 15个图标 -->
				<!-- 大卡片 -->
				<view class="bigCars">
					<view class="item" v-for="(item,index) in data.list5" :key="index" @click="toDetail(item)"
						:style="{backgroundColor: item.bgColor}">
						<view>
							<text :style="{color:item.color}">{{item.text1}}</text>
							<text>{{item.text2}}</text>
						</view>
						<view><img :src="item.img" alt=""></view>
					</view>
				</view>
				<!-- 大卡片 -->
			</view>
		</view>
		<!-- 主体内容 -->
	</view>
</template>

<script>
	import JsonData from "../../data/index.json"
	export default {
		data() {
			return {
				data: JsonData,
				onOffBanner: true,
				onOffMain: true,
				onOffTags: false,
				onOffMainContent: true,
				onOffMainTags: false,
				content: "",
				mainContent: "",
			}
		},
		methods: {
			headTagsClick(item) {
				console.log(item)
				if (item.index != 0) {
					this.onOffBanner = false
					this.onOffMain = false
					console.log(this)
				} else {
					this.onOffBanner = true
					this.onOffMain = true
				}
				this.content = item.name + "内容"
				if (item.index == 0) {
					this.onOffTags = false
				} else {
					this.onOffTags = true
				}
			},
			mainTagsClick(item) {
				console.log(item.name)
				if (item.index != 0) {
					this.onOffMainContent = false
					this.onOffMainTags = true
					console.log(this)
				} else {
					this.onOffMainContent = true
					this.onOffMainTags = false
				}
				this.mainContent = item.name + "内容"
			},
			toSearch() {
				uni.navigateTo({
					url: "/pages/index/search"
				})
			},
			toDetail(item) {
				console.log(item)
				uni.navigateTo({
					url: '/pages/index/detail?info=' + encodeURIComponent(JSON.stringify(item))
				})
			}
		}
	}
</script>

<style lang="less">
	.container {
		background-image: linear-gradient(to right, #0252ff, #00bbff);
		border-radius: 0 0 100rpx 100rpx;
		background-size: cover;
		height: 400rpx;

		.header {
			// .ztl {
			// 	height: 45rpx;
			// 	line-height: 45rpx;
			// 	color: white;
			// 	text-align: center;
			// }

			.inp {
				padding: 60rpx 20rpx 0;
				position: relative;

				img {
					position: absolute;
					width: 40rpx;
					height: 40rpx;
					top: 70rpx;
					left: 30rpx;
				}

				input {
					background-color: white;
					height: 60rpx;
					font-size: 26rpx;
					text-indent: 60rpx;
					border-radius: 30rpx;
				}
			}

			.tags {
				padding: 0 20rpx;
			}

		}

		.headerTagsContent {
			color: white;
			text-align: center;
			height: 150rpx;
			line-height: 150rpx;
			width: 90%;
			margin: 20rpx auto 0;
		}

		.mainTagsContent {
			color: black;
			text-align: center;
			height: 150rpx;
			line-height: 150rpx;
			width: 90%;
			margin: 20rpx auto 0;
		}


		.banner {
			width: 94%;
			height: 300rpx;
			margin: 10rpx auto;
			border-radius: 24rpx;
			color: white;
			overflow: hidden;
		}

		.main {
			.tags {
				padding-left: 10rpx;
			}

			.cars {
				width: 100%;
				display: flex;
				justify-content: center;
				flex-wrap: wrap;
				padding: 20rpx 0;

				.item {
					width: 18%;
					margin: 10rpx 5rpx;
					text-align: center;
					padding-top: 20rpx;
					font-size: 24rpx;
				}

				img {
					width: 80rpx;
					height: 80rpx;
				}
			}

			.bigCars {
				width: 100%;
				display: flex;
				justify-content: center;
				flex-wrap: wrap;
				padding: 30rpx 0 120rpx;

				.item {
					width: 30%;
					margin: 10rpx 10rpx;
					padding-bottom: 20rpx;
					border-radius: 12px;

					view:first-child {
						margin: 20rpx 0 20rpx 10rpx;

						text {
							display: block;
							font-size: 24rpx;
							color: #736c66;
							padding-top: 5rpx;
						}

						text:first-child {
							font-size: 38rpx;
						}
					}

					view:last-child {
						text-align: center;
					}
				}

				img {
					width: 140rpx;
					height: 140rpx;
				}
			}
		}
	}
</style>