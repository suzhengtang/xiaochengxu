<template>
	<view class="youhui">
		<view class="youhui-item" v-for="(item, index) in listArr" :key="index" @click="clickDetal(index)">
			<view class="left">
				<image mode="heightFix" :src="item.src"></image>
			</view>
			<view class="right">
				<view class="title">{{ item.title }}</view>
				<view class="content">
					<view class="content-left">位置：<span>{{ item.address }}</span></view>
					<view class="content-right">浏览量: <span>{{ item.number }}</span></view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listArr: [
					{
						title: '我很漂亮并且也很友好，和我交朋友的人都很幸运',
						address: '深圳',
						number: 100,
						src: '../../static/images/banner2.png'
					},
					{
						title: '我很漂亮并且也很友好',
						address: '北京',
						number: 200,
						src: '../../static/images/banner1.png'
					},
					{
						title: '我很漂亮并且也很友好，我很漂亮并且也很友好',
						address: '上海',
						number: 2020,
						src: '../../static/images/banner3.png'
					},
					{
						title: '我很漂亮并且也很友好，我很漂亮并且也很友好，我很漂亮并且也很友好，我很漂亮并且也很友好',
						address: '广州',
						number: 2001,
						src: '../../static/images/banner4.png'
					},
					{
						title: '我很漂亮并且也很友好，我很漂亮并且也很友好，我很漂亮并且也很友好，我很漂亮并且也很友好',
						address: '成都',
						number: 20101,
						src: '../../static/images/banner2.png'
					}
				]
			}
		},
		methods: {
			clickDetal(idx) {
				uni.showToast({
					title: `点击了第${idx+1}个`
				})
			}
		}
	}
</script>

<style lang="less">
.youhui {
	width: 750rpx;
	height: auto;
	background-color: #eee;
	padding: 20rpx;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	box-sizing: border-box;
	.youhui-item {
		width: 100%;
		height: 240rpx;
		display: flex;
		padding: 20rpx;
		box-sizing: border-box;
		background-color: #fff;
		margin-bottom: 20rpx;
		.left {
			width: 200rpx;
			height: 200rpx;
			margin-right: 20rpx;
			overflow: hidden;
			image {
				height: 200rpx;
			}
		}
		.right {
			width: 470rpx;
			height: 100%;
			position: relative;
			.content {
				width: 100%;
				height: 40rpx;
				position: absolute;
				left: 0;
				bottom: 0;
				display: flex;
				justify-content: space-between;
				.content-left, .content-right {
					color: #ccc;
					span {
						color: #ccc;
					}
				}
			}
		}
		&:last-child {
			margin-bottom: 0;
		}
	}
}
</style>
