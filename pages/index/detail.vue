<template>
	<view class="container">
		<view>
			<img :src="info.img" alt="">
			<view class="text">
				{{info.name?info.name:info.text1}}
				详情页
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				info: {}
			}
		},
		onLoad(options) {
			let info = JSON.parse(decodeURIComponent(options.info))
			console.log(info)
			this.info = info
		},
	}
</script>

<style lang="less">
	.container {
		view {
			text-align: center;
		}
	}
</style>