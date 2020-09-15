<template>
	<view>
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

		.common-list-1 {
			flex-shrink: 0; //防止被压缩

			image {
				width: 90rpx;
				height: 90rpx;
				border-radius: 100%;
			}
		}
	}
</style>
