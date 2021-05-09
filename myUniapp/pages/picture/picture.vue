<template>
	<view class="picture">
		<scroll-view class="left" scroll-y="true" :scroll-top="scrollTop">
			<view class="left-item" :class="index === current ? 'current' : ''" v-for="(item, index) in navList" :key="index" @click="itemClick(index)">{{item.title}}</view>
		</scroll-view>
		<scroll-view class="right" scroll-y="true" :scroll-top="scrollTop">
			<view class="right-item" v-for="(item, index) in detailsList" :key="index">
				<view class="item-img" @click="imgClick(index)">
					<image mode="widthFix" :src="item.url">{{ item.dir }}</image>
				</view>
				<view class="item-dir"></view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				scrollTop: 0,
				current: 0,
				navList: [
					{title: '家具生活', id: 1},
					{title: '古典美女', id: 2},
					{title: '明星帅哥', id: 3},
					{title: '明星美女', id: 4},
					{title: '朋友聚会', id: 5},
					{title: '年级聚会', id: 6},
					{title: '班级联系', id: 7},
					{title: '青村可爱', id: 8},
					{title: '房价山治', id: 9},
					{title: '周末玩耍', id: 10},
					{title: '学习进步', id: 11},
					{title: '心想事成', id: 12},
					{title: '梦想成真', id: 13},
					{title: '勤奋学习', id: 14},
					{title: '呵呵呵呵', id: 15}
				],
				detailsList: [
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/pic1.png', id: 1},
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/pic2.png', id: 2},
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/pic3.png', id: 3},
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/pic4.png', id: 4},
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/pic5.png', id: 5},
					{dir: '我是很漂亮的美女，我也非常的性感和迷人，同时我也很友好，喜欢交朋友', url: '../../static/images/picture.png', id: 6}
				]
			}
		},
		methods: {
			itemClick(idx) {
				this.current = idx
				this.detailsList[idx] && this.detailsList.push(this.detailsList[idx])
			},
			imgClick(idx) {
				// console.log(this.detailsList.map(item => item.url))
				uni.previewImage({
					current: idx,
					urls: this.detailsList.map(item => item.url)
				})
			}
		}
	}
</script>

<style lang="less">
page{ // 这个非常重要，没有设置将不能滚动
	height: 100%
}
.picture{
	width: 750rpx;
	height: 100%;
	display: flex;
	color: #666;
	font-size: 30rpx;
	background-color: #eee;
	.left {
		width: 200rpx;
		height: 100%;
		border-right: 1px solid #ddd;
		box-sizing: border-box;
		.left-item {
			width: 200rpx;
			height: 100rpx;
			line-height: 100rpx;
			background-color: #fff;
			border-bottom: 1px solid #ddd;
			text-align: center;
		}
		.current{
			background-color: #ed7043;
			color: #fff;
		}
	}
	.right {
		width: 550rpx;
		height: auto;
		padding: 10rpx;
		box-sizing: border-box;
		.right-item {
			width: 55orpx;
			background-color: #fff;
			padding-bottom: 20rpx;
			margin-bottom: 20rpx;
			.item-dir {
				padding: 0 20rpx;
				box-sizing: border-box;
			}
		}
		image {
			width: 550rpx;
		}
	}
}
</style>
