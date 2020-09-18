<template>
	<view>
		<!-- 模糊背景 -->
		<view class="topic-bg">
			<image :src="item.titlepic" mode="widthFix" lazy-load></image>
		</view>
		<!-- 话题信息 -->
		<view class="topic-info">
			<view class="topic-info-t u-f-ac">
				<image :src="item.titlepic" mode="widthFix" lazy-load></image>
				<view>#{{item.title}}#</view>
			</view>
			<view class="topic-info-c u-f-ac">
				<view>动态 {{item.totalnum}}</view>
				<view>今日 {{item.todaynum}}</view>
			</view>
			<view class="topic-info-b">
				{{item.desc}}
			</view>
		
		</view>
	</view>
</template>

<script>
	
	export default {
	
	
		props:{
			item:Object
		}
	}
</script>

<style lang="scss" scoped>
	.topic-bg {
			width: 100%;
			height: 300rpx;
			position: relative;
			overflow: hidden;
	
			>image {
				width: 100%;
				position: absolute;
				filter: blur(10px); //模糊化
			}
		}
	
		.topic-info {
			padding: 0 25rpx;
			position: relative;
	
			.topic-info-t {
				>image {
					width: 150rpx;
					height: 150rpx;
					border-radius: 20rpx;
					position: absolute;
					top: -75rpx;
				}
	
				>view {
					font-size: 35rpx;
					margin-left: 170rpx;
					flex: 1;
				}
			}
	
			.topic-info-c {
				padding: 35rpx 0 25rpx 0;
	
				view {
					color: #cdcdcd;
				}
			}
	
			.topic-info-b {
				color: #a3a3a3;
				font-size: 32rpx;
			}
		}
	
</style>
