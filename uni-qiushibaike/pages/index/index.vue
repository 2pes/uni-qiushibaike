<template>
	<view class="container">
		<block v-for="(item,index) in list" :key="index">
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
		</block>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{

					userpic: "../../static/demo/userpic/12.jpg", // 用户头像
					username: "昵称", // 用户昵称
					isguanzhu: false, // 是否关注
					title: "我是标题", // 标题
					type: "img", // img: 图文， video: 视频
					titlepic: "../../static/demo/datapic/11.jpg", // 标题图片
					playnum: "20w", // 播放次数
					long: "2:47", // 视频时长
					infonum: { // 点赞
						index: 0, // 0：没有操作  1：点赞 2： 踩
						dingnum: 11, // 点赞数量
						cainum: 11, // 踩
					},
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）

				}, {

					userpic: "../../static/demo/userpic/11.jpg", // 用户头像
					username: "昵称2", // 用户昵称
					isguanzhu: true, // 是否关注
					title: "我是标题", // 标题
					type: "vedio", // img: 图文， video: 视频
					titlepic: "../../static/demo/datapic/10.jpg", // 标题图片
					playnum: "10w", // 播放次数
					long: "3:47", // 视频时长
					infonum: { // 点赞
						index: 1, // 0：没有操作  1：点赞 2： 踩
						dingnum: 11, // 点赞数量
						cainum: 11, // 踩
					},
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）

				}]
			}
		},
		methods: {

		}

	}
</script>

<style lang="scss">
	.container {
		/* padding: 20px; */
		font-size: 14px;
		line-height: 24px;

		.index-list {
			padding: 20rpx;
			border-bottom: 1rpx solid #EEEEEE;
		}

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
