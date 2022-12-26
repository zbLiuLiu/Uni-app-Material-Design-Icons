<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 0rpx 40rpx;
	}
</style>
