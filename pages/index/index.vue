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
				<u-tabs :list="list1" @click="click" lineColor="white"
					:activeStyle="{color: 'white',fontWeight: '700',fontSize:'16px'}" :inactiveStyle="{color: 'white'}"
					itemStyle="padding:15rpx 20rpx"></u-tabs>
			</view>
			<!-- 选项卡 -->
		</view>
		<!-- 头部 -->
		<!-- 轮播图 -->
		<view class="banner">
			<u-swiper :list="list2" indicator indicatorMode="dot" indicatorStyle="dot" circular height="100%"
				bgColor="transparent" radius="12"></u-swiper>
		</view>
		<!-- 轮播图 -->
		<!-- 主体内容 -->
		<view class="main">
			<!-- 选项卡 -->
			<view class="tags">
				<view class="tags">
					<u-tabs :list="list3" @click="click" lineColor="red"
						:activeStyle="{color: 'red',fontWeight: '700',fontSize:'16px'}" :inactiveStyle="{color: 'black'}"
						itemStyle="padding:15rpx 20rpx"></u-tabs>
				</view>
			</view>
			<!-- 选项卡 -->
		</view>
		<!-- 主体内容 -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list1: [{
					name: '精选',
				}, {
					name: '美食',
				}, {
					name: '居家日用'
				}, {
					name: '女妆'
				}, {
					name: '美妆'
				}, {
					name: '数码家电'
				}, {
					name: '鞋品'
				}],
				list2: [
					'https://cdn.uviewui.com/uview/swiper/swiper3.png',
					'https://cdn.uviewui.com/uview/swiper/swiper2.png',
					'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				list3: [{
					name: '推荐',
				}, {
					name: '会员/卡券',
				}, {
					name: '会充'
				}]
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
			// background-color: white;
			color: white;
			text-align: center;
		}

		.inp {
			padding: 20rpx 20rpx 0;

			input {
				background-color: white;
				height: 60rpx;
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
		width: 700rpx;
		height: 300rpx;
		left: 50%;
		transform: translateX(-50%);
		border-radius: 24rpx;
		color: white;
		overflow: hidden;
	}

	.main {
		margin-top: 120rpx;
		background-color: skyblue;
		.tags{
			padding-left: 20rpx;
		}
	}
</style>