<template>
	<view class="content">
		<view class="banner">
			<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval">
				<swiper-item v-for="item in bannerImg" :key="item.id">
					<image :src="item.url"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="nav">
			<view class="nav-item" v-for="item in navData" :key="item.id" @click="itemClick(item.id)">
				<view class="icon" :class="item.color"></view>
				<text class="icon-text">{{item.text}}</text>
			</view>
		</view>
		<view class="tuijian">
			推荐商品
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bannerImg: [
					{img: '图片一', url: '../../static/images/banner1.png', id: 1},
					{img: '图片二', url: '../../static/images/banner2.png', id: 2},
					{img: '图片三', url: '../../static/images/banner3.png', id: 3},
					{img: '图片四', url: '../../static/images/banner4.png', id: 4}
				],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				navData: [
					{text: '正堂练习', id: 11, color: "red"},
					{text: '联系我们', id: 12, color: "yellow"},
					{text: '社区图片', id: 13, color: "pink"},
					{text: '学习视频', id: 14, color: "skyblue"},
				]
			}
		},
		onLoad() {
			console.log(123)
		},
		methods: {
			itemClick(par) {
				console.log(par)
			}
		}
	}
</script>

<style>
	.content {
		width: 100%;
		height: 100%;
		background-color: #eee;
		overflow: hidden;
	}
	.content .nav {
		width: 750rpx;
		height: 200rpx;
		background-color: #fff;
		display: flex;
		justify-content: space-between;
		align-items: center;
		text-align: center;
	}
	.content .nav .icon {
		display: inline-block;
		width: 100rpx;
		height: 100rpx;
		background-color: #007AFF;
		border-radius: 50%;
	}
	.content .nav .red {
		background-color: #ffaa00
	}
	.content .nav .yellow {
		background-color: #aaaaff
	}
	.content .nav .pink {
		background-color: pink
	}
	.content .nav .skyblue {
		background-color: skyblue
	}
	.content .nav .icon-text {
		font-size: 12px;
		color: #333;
		display: inline-block;
	}
	.content .tuijian{
		margin: 8px 0;
		width: 750rpx;
		height: 90rpx;
		line-height: 90rpx;
		background-color: #fff;
		color: #ed7043;
		letter-spacing: 60rpx;
		text-align: center;
	}
</style>
