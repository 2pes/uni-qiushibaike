<template>
	<view class="common-list u-f">
		<view class="common-list-l">
			<image src="../../static/demo/userpic/10.jpg" mode="widthFix" lazy-load></image>
		</view>
		<view class="common-list-r">
			<view class="u-f-ac u-f-jsb">
				<view class="u-f-ac">{{item.username}}
					<view class="tag-sex icon iconfont" :class="[item.sex==0?' icon-nan':'icon-nv']">{{item.age}}</view>
				</view>
				<view v-show="!isguanzhu" @tap="guanzhu" class="icon iconfont icon-zengjia">关注</view>
			</view>
			<view>{{item.title}}</view>
			<view class="u-f-ajc">
				<image v-if="item.titlepic" :src="item.titlepic" mode="widthFix" lazy-load></image>
				<!-- 视频 -->
				<template v-if="item.video">
					<view class="icon iconfont icon-bofang index-list-play"></view>
					<view class="index-list-playinfo">{{item.video.playnum}} 次播放 {{item.video.long}}</view>
				</template>

				<view v-if="item.share" class="common-list-share u-f-ac">
					<image :src="item.share.titlepic" mode="widthFix" lazy-load></image>
					<view>{{item.share.title}}</view>
				</view>

			</view>
			<view class="u-f-ac u-f-jsb">
				<view>{{item.path}}</view>
				<view class="u-f u-f-jsb">
					<view class="icon iconfont icon-zhuanfa">{{item.sharenum}}</view>
					<view class="icon iconfont icon-pinglun1">{{item.commentnum}}</view>
					<view class="icon iconfont icon-dianzan1">{{item.goodnum}}</view>
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
		},
		data() {
			return {
				isguanzhu: this.item.isguanzhu,
				infonum: this.item.infonum
			}
		},
		methods: {
			//关注
			guanzhu() {
				this.isguanzhu = true;
				uni.showToast({
					title: "关注成功"

				})
			},
		}
	}
</script>

<style lang="scss" scoped>
	.common-list {
		padding: 20rpx;

		.common-list-l {
			flex-shrink: 0; //文字标题防止被压缩

			image {
				width: 90rpx;
				height: 90rpx;
				border-radius: 100%;
			}
		}

		.common-list-r {
			flex: 1;
			margin-left: 15rpx;
			border-bottom: 1rpx solid #EEEEEE;
			padding-bottom: 10rpx;

			>view:nth-child(3)>image {
				width: 100%;
				border-radius: 10rpx;
			}

			>view:nth-child(1)>view:first-child {
				color: #999999;
				font-size: 32rpx;
			}

			>view:nth-child(1)>view:last-child {
				background: #EEEEEE;
				padding: 0 10rpx;
				font-size: 26rpx;
			}

			.tag-sex {
				background: #007AFF;
				color: #FFFFFF;
				font-size: 23rpx;
				padding: 5rpx 10rpx;
				margin-left: 10rpx;
				border-radius: 20rpx;
				line-height: 22rpx;
			}

			>view:nth-child(2) {
				font-size: 32rpx;
				padding: 12rpx 0;
			}

			>view:nth-child(3) {
				position: relative;

				.index-list-play {
					position: absolute;
					font-size: 140rpx;
					color: #FFFFFF;
				}

				.index-list-playinfo {
					position: absolute;
					background: rgba(51, 51, 51, 0.72);
					bottom: 10rpx;
					right: 10rpx;
					border-radius: 40rpx;
					color: #FFFFFF;
					font-size: 22rpx;
					padding: 0 10rpx;
				}

				.common-list-share {
					background: #EEEEEE;
					width: 100%;
					padding: 10rpx;
					border-radius: 10rpx;

					>image {
						width: 200rpx;
						height: 150rpx;
						margin-right: 10rpx;
					}
				}
			}

			>view:nth-child(4) {
				>view {
					color: #AAAAAA;
				}


				>view:nth-child(2)>view {
					margin-left: 10rpx;
					padding-left: 5rpx;
				}
			}
		}
	}
</style>
