<template>
	<view class="topic-news animated fadeInLeft fast">
		<view class="">最近更新</view>
		<block v-for="(item,index) in list" :key="index">
			<view class="topic-list u-f">
				
				<image :src="item.titlepic" mode="widthFix" lazy-load>
			
				</image>
				<view>
					<view>{{item.title}}</view>
					<view>{{item.desc}}</view>
					<view>动态 {{item.totalnum}} 今日 {{item.todaynum}}</view>
				</view>
			</view>
		</block>
		
	</view>
</template>

<script>
	
	export default {
		props:{
			list:Array
		}
	}
</script>


<style lang="scss" scoped>
	.topic-news {
		padding: 20rpx;
	
		>view:first-child {
			padding-bottom: 5rpx;
			font-size: 32rpx;
		}
	
		
		.topic-list {
			padding: 20rpx 0;
			border-bottom: 1rpx solid #EEEEEE;
			image {
				width: 150rpx;
				height: 150rpx;
				border-radius: 10rpx;
				margin-right: 10rpx;
			}
			
		
	
			>view {
				color: #A4a4a4;
	
				>view:first-child {
					color: #333333;
					font-size: 32rpx;
				}
			}
		}
	}
</style>
