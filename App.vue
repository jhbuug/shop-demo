<script>
	export default {
		onLaunch: function() {
			var topBar = uni.getSystemInfoSync()
			console.log(topBar)
		}
	}
</script>
<style lang="scss">
	@import "@/uni_modules/uview-ui/index.scss";

	page {
		background-color: #f0f0f0;
	}
</style>