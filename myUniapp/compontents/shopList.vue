<template>
	<view class="main-item">
		<view class="item-one" v-for="(item, index) in dataList" :key="index" @click="detailsItem(item)">
			<view class="one-img">
				<image class="one-img-img" mode="widthFix" src="../static/images/meinv.png"></image>
			</view>
			<view class="one-dir">
				<view class="dir-top"><span>美女</span><span class="remove-el">帅哥</span></view>
				<view class="dir-bottom">我很漂亮并且也很友好，和我交朋友的人都很幸运</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			dataList: {
				type: Array,
				default: []
			}
		},
		data() {
			return {
				
			}
		},
		methods: {
			detailsItem(item) {
				this.$emit('detailsItemFn', item)
			}
		}
	}
</script>

<style>
	.main-item {
		padding: 0 0 20rpx 20rpx;
		display: flex;
		flex-wrap: wrap;
	}
	.main-item .item-one {
		width: 345rpx;
		background-color: #fff;
		padding: 30rpx;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;
		box-sizing: border-box;
		margin: 0 20rpx 20rpx 0;
	}
	.main-item .item-one .one-img {
		width: 100%;
		text-align: center;
	}
	.main-item .item-one .one-img .one-img-img{
		width: 100%;
	}
	.main-item .item-one .one-dir{
		color: #666;
		font-size: 30rpx;
	}
	.main-item .item-one .one-dir .dir-top{
		color: #ed7043;
		font-size: 34rpx;
	}
	.main-item .item-one .one-dir .dir-top .remove-el{
		color: #ccc;
		font-size: 30rpx;
		margin-left: 30rpx;
		text-decoration: line-through;
		
	}
	.main-item .item-one .one-dir .dir-bottom{
		text-overflow: ellipsis;
		overflow: hidden;
		display: -webkit-box;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
		margin-top: 20rpx;
	}
</style>
