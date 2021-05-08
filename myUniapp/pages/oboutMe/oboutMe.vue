<template>
	<view class="about-me">
		<view class="me-img">
			<image mode="widthFix" src="../../static/images/aboutMe.png"></image>
		</view>
		<view class="me-phone">
			联系电话： <span @click="phoneClick">0755-8888888(点击拨打)</span>
		</view>
		<view class="me-address">地址：深圳市罗湖区京基100大厦深圳市罗湖区京基100大厦深圳市罗湖区京基100大厦深圳市罗湖区京基100大厦</view>
		<view class="me-map"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			phoneClick() {
				uni.makePhoneCall({
					phoneNumber: '0755-8888888'
				})
			}
		}
	}
</script>

<style lang="less">
.about-me {
	width: 100%;
	height: auto;
	.me-img{
		width: 100%;
		height: 375rpx;
		overflow: hidden;
		image{
			width: 100%;
		}
	}
	.me-phone, .me-address{
		width: 100%;
		padding-left: 20rpx;
		box-sizing: border-box;
		color: #666;
		font-size: 30rpx;
		border-bottom: 1px solid #ddd;
		padding-top: 30rpx;
		padding-bottom: 30rpx;
	}
	.me-address {
		line-height: 46rpx;
		height: auto;
	}
}
</style>
