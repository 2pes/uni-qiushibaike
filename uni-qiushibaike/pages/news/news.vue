<template>
	<view>
		<news-nav-bar :tabBars="tabBars" :tabIndex="tabIndex" @change-tab="changeTab"></news-nav-bar>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item>
					<scroll-view scroll-y class="list" @scrolltolower="loadmore()">
						<!-- 列表 -->
						<block v-for="(item,index) in guanzhu.list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						<!-- 加载更多 -->
						<load-more :loadtext="guanzhu.loadtext"></load-more>
					</scroll-view>
				</swiper-item>
				<!-- 话题 -->
				<swiper-item>
					<scroll-view scroll-y class="list">
						<!-- 搜索-->
						<view class="search-input">
							<input class="uni-input" placeholder-class="icon iconfont icon-sousuo topic-search" placeholder="搜索内容">
						</view>

						<!-- 轮播 -->
						<view>
							<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
								<block v-for="(item ,index) in topic.swiper" :key="index">
									<swiper-item>
										<image :src="item.src" mode="widthFix" lazy-load></image>
									</swiper-item>
								</block>


							</swiper>
						</view>
						<!-- 热门分类 -->
						<topic-nav :nav="topic.nav"></topic-nav>
						<!-- 最近更新 -->
						<view class="topic-news ">
							<view class="">最近更新</view>
							<block v-for="(item,index) in topic.list" :key="index">
								<topic-list :item="item" :index="index"></topic-list>
							</block>
						</view>
						<!-- <block v-for="(item,index) in list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						
						<load-more :loadtext="items.loadtext"></load-more> -->
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>

	</view>
</template>

<script>
	import newsNavBar from '../../components/news/news-nav-bar.vue';
	import commonList from '../../components/common/common-list.vue';
	import loadMore from "../../components/common/load-more.vue";
	import topicNav from '../../components/news/topic-nav.vue';
	import topicList from '../../components/news/topic-list.vue';
	export default {
		components: {
			newsNavBar,
			commonList,
			loadMore,
			topicNav,
			topicList
		},
		data() {
			return {
				swiperHeight: 500,
				tabIndex: 0,
				tabBars: [{
					name: '关注',
					id: "guanzhu"
				}, {
					name: "话题",
					id: "topic"
				}],
				guanzhu: {
					loadtext: "上拉加载更多",
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
				},

				topic: {
					swiper: [{
						src: "../../static/demo/banner1.jpg"
					}, {
						src: "../../static/demo/banner2.jpg"
					}, {
						src: "../../static/demo/banner3.jpg"
					}],
					nav: [{
								name: "最新"
							},
							{
								name: "游戏"
							},
							{
								name: "打卡"
							},
							{
								name: "情感"
							},
							{
								name: "故事"
							},
							{
								name: "喜爱"
							}
						]

						,
					list: [{
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/1.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/2.jpeg',
						desc: '话题描述话题描述话题描述话题描述描述话题描述描述话题描述描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}, {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}]
				}
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100);
					this.swiperHeight = height;
				}
			})
		},
		methods: {
			//上拉加载
			loadmore() {
				if (this.guanzhu.loadtext != '上拉加载更多') {
					return;
				}
				this.guanzhu.loadtext = "加载中...";
				setTimeout(() => {
					//获取数据
					var obj = {
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

					}
					this.guanzhu.list.push(obj);
					this.guanzhu.loadtext = "上拉加载更多";
				}, 1000)


				// this.guanzhu.loadtext = "没有更多数据了";
			},

			openAdd() {
				uni.navigateTo({
					url: '../add-input/add-input'
				})
			},
			//点击切换
			changeTab(index) {
				this.tabIndex = index;
			},
			//滑动切换
			tabChange(e) {
				this.tabIndex = e.detail.current;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.search-input {
		padding: 20rpx;

		>input {
			border-radius: 10rpx;
			background: #f4f4f4;
		}

		.topic-search {
			display: flex;
			justify-content: center;
			font-size: 27rpx;
		}
	}

	.topic-swiper {
		padding: 0 20rpx 20rpx 20rpx;

		image {
			width: 100%;
			border-radius: 10rpx;
		}
	}

	.topic-news {
		padding: 20rpx;

		>view:first-child {
			padding-bottom: 5rpx;
			font-size: 32rpx;
		}
	}
</style>
