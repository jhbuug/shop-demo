<template>
	<view>
		<!-- 头部 -->
		<view class="header">
			<view class="ztl">状态栏</view>
			<view class="inp">
				<input type="text" placeholder="请输入关键字">
			</view>
			<!-- 选项卡 -->
			<view class="tags">
				<u-tabs :list="data.list1" @click="click" lineColor="white"
					:activeStyle="{color: 'white',fontWeight: '700',fontSize:'26rpx'}"
					:inactiveStyle="{color: 'white',fontSize:'24rpx'}" itemStyle="padding:15rpx 15rpx"></u-tabs>
			</view>
			<!-- 选项卡 -->
		</view>
		<!-- 头部 -->
		<!-- 轮播图 -->
		<view class="banner">
			<u-swiper :list="data.list2" indicator indicatorMode="dot" indicatorStyle="dot" circular height="100%"
				bgColor="transparent" radius="12"></u-swiper>
		</view>
		<!-- 轮播图 -->
		<!-- 主体内容 -->
		<view class="main">
			<!-- 选项卡 -->
			<view class="tags">
				<view class="tags">
					<u-tabs :list="data.list3" @click="click" lineColor="red"
						:activeStyle="{color: 'red',fontWeight: '700',fontSize:'26rpx'}"
						:inactiveStyle="{color: 'black',fontSize:'24rpx'}" itemStyle="padding:15rpx 15rpx"></u-tabs>
				</view>
			</view>
			<!-- 选项卡 -->
			<!-- 15个图标 -->
			<view class="cars">
				<view class="item" v-for="(item,index) in data.list4" :key="index">
					<img :src="item.img" alt="">
					<view>{{item.name}}</view>
				</view>
			</view>
			<!-- 15个图标 -->
			<!-- 大卡片 -->
			<view class="bigCars">
				<view class="item" v-for="(item,index) in data.list5" :key="index"
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
		<!-- 主体内容 -->
	</view>
</template>

<script>
	import JsonData from "../../data/index.json"
	// console.log(JsonData.list1)
	export default {
		data() {
			return {
				data: JsonData
			}
		},
		methods: {
			click(item) {
				console.log('item', item);
			}
		}
	}
</script>

<style lang="less">
	.header {
		height: 400rpx;
		background-image: linear-gradient(to right, #0252ff, #00bbff);
		border-radius: 0 0 100rpx 100rpx;

		.ztl {
			height: 45rpx;
			line-height: 45rpx;
			color: white;
			text-align: center;
		}

		.inp {
			padding: 20rpx 20rpx 0;

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

	.banner {
		position: absolute;
		top: 210rpx;
		width: 94%;
		height: 300rpx;
		left: 50%;
		transform: translateX(-50%);
		border-radius: 24rpx;
		color: white;
		overflow: hidden;
	}

	.main {
		margin-top: 120rpx;

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
			padding: 30rpx 0;
			background-color: #00bbff;

			.item {
				width: 30%;
				margin: 10rpx 10rpx;
				padding-bottom: 20rpx;
				border-radius: 12px;

				view:first-child {
					margin: 20rpx 0 20rpx 10rpx;

					text {
						display: block;
						font-size: 24rpx
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
				background-color: #0252ff;
			}
		}
	}
</style>