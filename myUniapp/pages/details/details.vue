<template>
	<view class="details">
		我是id为 <span class="import-num">{{ number }}</span> 的商品详情页面
		<view class="btn-bottom">
			<uni-goods-nav :fill="true"  :options="options" :buttonGroup="buttonGroup"  @click="onClick" @buttonClick="buttonClick" />
		</view>
	</view>
</template>

<script>
	import uniGoodsNav from '@/uni_modules/uni-goods-nav/components/uni-goods-nav/uni-goods-nav.vue'
	export default {
		components:{
			uniGoodsNav
		},
		data() {
			return {
				number: 0,
				options: [{
					icon: 'headphones',
					text: '客服'
				}, {
					icon: 'shop',
					text: '店铺',
					info: 2,
					infoBackgroundColor:'#007aff',
					infoColor:"red"
				}, {
					icon: 'cart',
					text: '购物车',
					info: 2
				}],
				buttonGroup: [{
				  text: '加入购物车',
				  backgroundColor: '#ff0000',
				  color: '#fff'
				},
				{
				  text: '立即购买',
				  backgroundColor: '#ffa200',
				  color: '#fff'
				}]
			}
		},
		methods: {
			onClick (e) {
				uni.showToast({
				  title: `点击${e.content.text}`,
				  icon: 'none'
				})
			  },
			  buttonClick (e) {
				console.log(e)
				if (e.index === 0) {
					this.options[2].info++
				}
				else {
					uni.showToast({
						title: `立即购买`,
						icon: 'none'
					})
				}
			}
		},
		onLoad(params) {
			// console.log(params)
			this.number = params.id
		}
	}
</script>

<style lang="less">
.details{
	width: 100%;
	text-align: center;
	padding-top: 100rpx;
	color: #666;
	.btn-bottom {
		width: 100%;
		height: auto;
		position: fixed;
		left: 0;
		bottom: 0;
		border-top: 1px solid #ddd;
	}
}
.details .import-num{
	color: #ed7043;
	padding: 0 20rpx;
	font-size: 34rpx;
	font-weight: 900;
}
</style>
