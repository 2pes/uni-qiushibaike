<template>
	<view class="index-list">
		<view class="index-list1 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<image :src="item.userpic" mode="widthFix" lazy-load></image>{{item.username}}
			</view>

			<view class="u-f-ac" v-show="item.isguanzhu">
				<view class="icon iconfont icon-zengjia"></view>关注
			</view>
		</view>
		<view class="index-list2">{{item.title}}</view>
		<view class="index-list3 u-f-ajc">
			<image :src="item.titlepic" mode="widthFix" lazy-load></image>
			<!-- 视频 -->
			<template v-if="item.type=='video'">
				<view class="icon iconfont icon-zengjia index-list-play"></view>
				<view class="index-list-playinfo">{{item.playnum}}万次播放 {{item.long}}</view>
			</template>

		</view>
		<view class="index-list4 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<view class="u-f-ac " :class="{'active':(item.infonum.index==1)}">
					<view class="icon iconfont icon-zengjia"></view>{{item.infonum.dingnum}}

				</view>
				<view class="u-f-ac" :class="{'active':(item.infonum.index==2)}">
					<view class="icon iconfont icon-zengjia"></view>{{item.infonum.cainum}}
				</view>
			</view>
			<view class="u-f-ac">
				<view class="u-f-ac">
					<view class="icon iconfont icon-pinglun"></view>{{item.commentnum}}

				</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zengjia"></view>{{item.sharenum}}
				</view>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		props: {
			item: Object,
			index: Number
		}
	}
</script>

<style lang="scss" scoped>
	.index-list {
		padding: 20rpx;
		border-bottom: 1rpx solid #EEEEEE;

		.index-list1 {
			view:first-child {
				color: #999999;
			}

			view:first-child image {
				width: 85rpx;
				height: 85rpx;
				border-radius: 100%;
				margin-right: 10rpx;
			}

			view:last-child {
				background: #F4F4F4;
				border-radius: 2rpx;
				padding: 0 10rpx;
			}
		}

		.index-list2 {
			padding-top: 15rpx;
			font-size: 32rpx;
		}

		.index-list3 {
			padding-top: 15rpx;
			position: relative;

			image {
				width: 100%;
				border-radius: 20rpx;
			}

			.index-list-play {
				position: absolute;
				font-size: 140rpx;
				color: #FFFFFF;
			}

			.index-list-playinfo {
				position: absolute;
				background: rgba(51, 51, 51, 0.72);
				bottom: 8rpx;
				right: 8rpx;
				border-radius: 40rpx;
				color: #FFFFFF;
				font-size: 22rpx;
				padding: 0 10rpx;
			}
		}

		.index-list4 {
			padding: 15rpx 0;

			.active {
				view {
					color: #0081FF;
				}
			}

			view {
				color: #999999;

				view {

					view,
					view:first-child {
						margin-right: 10rpx;
					}


				}
			}
		}
	}
</style>
