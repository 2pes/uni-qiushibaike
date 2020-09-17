<template>
	<view class="topic-nav">
		<view class="u-f-ac u-f-jsb">
			<view>热门分类</view>
			<view class="u-f-ac">
				更多<view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="u-f-ac">
			<block v-for="(item,index) in nav" :key="index">
				<view class="u-f-ajc">{{item.name}}</view>
			</block>
		
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			nav:Array
		}
	}
</script>

<style lang="scss" scoped>
	.topic-nav {
			border-bottom: 1rpx solid #EEEEEE;
			border-top: 1rpx solid #EEEEEE;
			padding: 20rpx;
	
			>view:first-child {
				margin-bottom: 10rpx;
				view {
					color: #9e9e9e;
				}
				>view:first-child {
					color: #333333;
					font-size: 32rpx;
				}
			}
	
			>view:last-child {
				>view {
					flex: 1; //平均分配
					background: #EEEEEE;
					color: #9e9e9e;
					border-radius: 10rpx;
					margin: 0 10rpx;
				}
			}
	
		}
	
</style>
