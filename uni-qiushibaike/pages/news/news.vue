<template>
	<view>
		<!-- 头部导航 -->
		<uni-nav-bar fixed="true" :statusBar="true" @clickRight="openAdd">
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
		<block v-for="(item,index) in list" :key="index">
			<common-list :item="item" :index="index"></common-list>
		</block>

	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
	import commonList from '../../components/common/common-list.vue';
	export default {
		components: {
			uniNavBar,commonList
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
				}],
				list: [{

					userpic: "../../static/demo/userpic/11.jpg", // 用户头像
					username: "hhh2", // 用户昵称
					isguanzhu: false, // 是否关注
					sex: 0,
					age: 25,
					title: "我是标题", // 标题
					video: false,
					share: false,
					path: "深圳 龙岗",
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）
					goodnum: 10,

				}, {

					userpic: "../../static/demo/userpic/11.jpg", // 用户头像
					username: "hhh2", // 用户昵称
					isguanzhu: false, // 是否关注
					sex: 0,
					age: 25,
					title: "我是标题", // 标题
					video: false,
					titlepic: "../../static/demo/datapic/10.jpg", // 标题图片
					share: false,
					path: "深圳 龙岗",
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）
					goodnum: 10,

				}, {

					userpic: "../../static/demo/userpic/11.jpg", // 用户头像
					username: "hhh2", // 用户昵称
					isguanzhu: true, // 是否关注
					sex: 1,
					age: 25,
					title: "我是标题", // 标题
					video: {
						looknum: "20w",
						long: "2:33"
					},
					titlepic: "../../static/demo/datapic/10.jpg", // 标题图片
					share: false,
					path: "深圳 龙岗",
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）
					goodnum: 10,

				}, {

					userpic: "../../static/demo/userpic/11.jpg", // 用户头像
					username: "hhh2", // 用户昵称
					isguanzhu: true, // 是否关注
					sex: 1,
					age: 25,
					title: "我是标题", // 标题
					video: false,
					titlepic: "", // 标题图片
					share: {
						titlepic: "../../static/demo/datapic/10.jpg", // 标题图片
						title: "我是标题" // 标题
					},
					path: "深圳 龙岗",
					commentnum: 0, // 评论
					sharenum: 11, // 转发（分享）
					goodnum: 10,

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

</style>
