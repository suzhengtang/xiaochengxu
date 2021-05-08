<template>
	<view class="content">
		<view class="banner">
			<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval">
				<swiper-item v-for="item in bannerImg" :key="item.id">
					<image class="banner-img" :src="item.url"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="nav">
			<view class="nav-item" v-for="item in navData" :key="item.id" @click="itemClick(item.id)">
				<view class="icon" :class="item.color"></view>
				<text class="icon-text">{{ item.text }}</text>
			</view>
		</view>
		<view class="tuijian">
			{{ title }}
		</view>
		<shop-list :dataList="itemArr" @detailsItemFn="detailsItemFn"></shop-list>
		<view class="tip-show" v-show="tipShow">-----我是有底线的-----</view>
	</view>
</template>

<script>
	import shopList from '../../compontents/shopList.vue'
	export default {
		components: {
			shopList
		},
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
					{text: '商品列表', id: 11, color: "red"},
					{text: '联系我们', id: 12, color: "yellow"},
					{text: '社区图片', id: 13, color: "pink"},
					{text: '学习视频', id: 14, color: "skyblue"},
				],
				title: '推荐商品',
				itemArr: [1,2,3,4,5,6,7,8,9,0],
				tipShow: false
			}
		},
		onLoad() {
			console.log(123)
		},
		methods: {
			itemClick(par) {
				switch(par){
					case 11:
						// console.log('商品列表')
						uni.navigateTo({
							url: '/pages/goodsList/goodsList'
						})
						break
					case 12:
						uni.navigateTo({
							url: '/pages/oboutMe/oboutMe'
						})
						break
					case 13:
						uni.navigateTo({
							url: '/pages/picture/picture'
						})
						break
					case 14:
						console.log('学习视频')
						break
				}
			},
			detailsItemFn(item) {
				uni.navigateTo({
					url: '/pages/details/details?id=' + item
				})
			}
		},
		onPullDownRefresh() { //手动触发下拉刷新
			setTimeout(function() {
				uni.stopPullDownRefresh()
				uni.showToast({
					title: '刷新成功'
				})
			}, 1000)
		},
		onReachBottom() { // 页面滚动到底部的事件
			if (this.itemArr.length < 14) {
				setTimeout(() => {
					uni.showToast({
						title: '加载中'
					})
					this.itemArr = [...this.itemArr, ...[11, 12, 13, 14]]
				},1000)
			} else {
				this.tipShow = true
			}
		}
	}
</script>

<style lang="less">
	.content {
		width: 100%;
		height: 100%;
		background-color: #eee;
		overflow: hidden;
		.banner {
			width: 100%;
			height: 375rpx;
			.swiper {
				height: 375rpx;
				.banner-img{
					width: 100%;
					height: 375rpx;
				}
			}
		}
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
		font-size: 30rpx;
		color: #666;
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
	.content .tip-show{
		text-align: center;
		margin-bottom: 30rpx;
		color: #ccc;
		font-size: 30rpx;
	}
</style>
