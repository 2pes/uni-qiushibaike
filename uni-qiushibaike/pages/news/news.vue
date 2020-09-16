<template>
	<view>
		<!-- 头部导航 -->
		<uni-nav-bar :statusBar="true" @clickRight="openAdd">
			<!-- 左边 -->
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<!-- 中间 -->
			<view class="nav-tab-bar u-f-ajc">
				<block v-for="(tab,index) in tabBars" :key="tab.id">
					<view class="u-f-ajc" :class="{'active':tabIndex==index}" @tap="changeTab(index)">{{tab.name}}
						<view v-if="(tabIndex==index)" class="nav-tab-bar-line"></view>
					</view>
				</block>


			</view>
			<!-- 右边 -->
			<block slot="right">
				<view class="nav-right u-f-ajc">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>
		<!-- 列表 -->

		<view class="common-list u-f">
			<view class="common-list-l">
				<image src="../../static/demo/userpic/10.jpg" mode="widthFix" lazy-load></image>
			</view>
			<view class="common-list-r">
				<view class="u-f-ac u-f-jsb">
					<view class="u-f-ac">昵称<view class="tag-sex icon iconfont icon-nan">25</view>
					</view>
					<view class="icon iconfont icon-zengjia">关注</view>
				</view>
				<view>我是标题我是标题我是标题我是标题我是标题我是标题我是标题我是标题我是标题我是标题</view>
				<view class="u-f-ajc">
			<!-- 		<image src="../../static/demo/datapic/13.jpg" mode="widthFix" lazy-load></image>
					<view class="icon iconfont icon-bofang index-list-play"></view>
					<view class="index-list-playinfo">22w万次播放 23:23</view> -->
					<view class="common-list-share u-f-ac">
						<image src="../../static/demo/datapic/14.jpg" mode="widthFix" lazy-load></image>
					<view>我是标题我是标题我是标题我是标题我是标题我是标题我是标题我是标题我是标题</view>
					</view>
					
				</view>
				<view class="u-f-ac u-f-jsb">
					<view>深圳 龙岗</view>
					<view class="u-f u-f-jsb">
						<view class="icon iconfont icon-zhuanfa">10</view>
						<view class="icon iconfont icon-pinglun1">20</view>
						<view class="icon iconfont icon-dianzan1">20</view>
					</view>
				</view>
			</view>

		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	export default {
		components: {
			uniNavBar
		},
		data() {
			return {
				tabIndex: 0,
				tabBars: [{
					name: '关注',
					id: "guanzhu"
				}, {
					name: "话题",
					id: "topic"
				}]
			}
		},
		methods: {
			openAdd() {
				uni.navigateTo({
					url: '../add-input/add-input'
				})
			},
			changeTab(index) {
				this.tabIndex = index;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.nav-left,
	.nav-right {

		>view {
			font-size: 40rpx;
		}
	}

	.nav-left {
		margin-left: 16rpx;

		>view {
			color: #FFF9619;
		}
	}

	.nav-right {
		margin-right: 5rpx;
		width: 100%;
	}

	.nav-tab-bar {
		width: 100%;
		margin-left: -20rpx;
		position: relative;

		>view {
			font-size: 32rpx;
			padding: 0 15rpx;
			font-weight: bold;
			color: #969696;

		}

		.active {
			color: #333333 !important;

			.nav-tab-bar-line {
				border-bottom: 5rpx solid #FEDE33;
				border-top: 5rpx solid #FEDE33;
				width: 70rpx;
				border-radius: 20rpx;
				position: absolute;
				bottom: 0rpx;
			}
		}
	}

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
				.common-list-share{
					background: #EEEEEE;
					width: 100%;
					padding: 10rpx;
					border-radius: 10rpx;
					>image{
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
