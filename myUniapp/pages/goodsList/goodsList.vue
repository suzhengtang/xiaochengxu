<template>
	<view class="goods-list">
		<shop-list :dataList="dataLists" @detailsItemFn="detailsItemFn"></shop-list>
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
				dataLists: [1,2,3,4,5,6,7,8,9,0,11,12,13,14,15,16,17,18,19],
				tipShow: false
			}
		},
		methods: {
			detailsItemFn(item){
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
		onReachBottom() {
			if (this.dataLists.length < 20) {
				setTimeout(() => {
					uni.showToast({
						title: '加载中'
					})
					this.dataLists = [...this.dataLists, ...[11, 12, 13, 14]]
				},1000)
			} else {
				this.tipShow = true
			}
		}
	}
</script>

<style>
.goods-list{
	width: 100%;
	height: auto;
	background-color: #eee;
	padding-bottom: 30rpx;
}
.goods-list .tip-show{
	text-align: center;
	margin-bottom: 30rpx;
	color: #ccc;
	font-size: 30rpx;
}
</style>
