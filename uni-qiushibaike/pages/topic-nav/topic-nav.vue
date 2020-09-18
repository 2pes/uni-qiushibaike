<template>
	<view>
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length>0">
							<!-- 话题列表 -->
							<view class="topic-view">
								<block v-for="(item,index1) in items.list" :key="index1">
									<topic-list :item="item" :index="index1"></topic-list>
								</block>
							</view>
							<!-- 加载更多 -->
							<load-more :loadtext="items.loadtext"></load-more>
						</template>

						<template v-else>
							<!-- 默认无内容 -->
							<no-thing></no-thing>
						</template>

					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	import loadMore from "../../components/common/load-more.vue";
	import noThing from "../../components/common/no-thing.vue";
	import topicList from '../../components/news/topic-list.vue';
	export default {
		components: {

			swiperTabHead,
			loadMore,
			noThing,
			topicList

		},
		data() {
			return {
				swiperHeight: 500,
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "1",
						num: 10
					},
					{
						name: "推荐",
						id: "2"
					},
					{
						name: "体育",
						id: "3"
					},
					{
						name: "热点",
						id: "4"
					},
					{
						name: "财经",
						id: "5"
					},
					{
						name: "新闻",
						id: "6"
					}
				],
				newsList: [{
					loadtext: "上拉加载更多",
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
				}, {
					loadtext: "上拉加载更多",
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
					}]
				}, {
					loadtext: "上拉加载更多",
					list: [{
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
				}, {
					loadtext: "上拉加载更多",
					list: []
				}, {
					loadtext: "上拉加载更多",
					list: []
				}, {
					loadtext: "上拉加载更多",
					list: []
				}],

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
			loadmore(index) {
				console.log(index);
				if (this.newsList[index].loadtext != '上拉加载更多') {
					return;
				}
				this.newsList[index].loadtext = "加载中...";
				setTimeout(() => {
					//获取数据
					var obj = {
						title: '#话题名称#',
						titlepic: '../../static/demo/topicpic/3.jpeg',
						desc: '话题描述话题描述话题描述话题描述',
						totalnum: 50,
						todaynum: 10
					}
					this.newsList[index].list.push(obj);
					this.newsList[index].loadtext = "上拉加载更多";
				}, 1000)


				// this.newsList[index].loadtext = "没有更多数据了";
			},

			tabtap(index) {
				this.tabIndex = index;
			},
			tabChange(e) {
				this.tabIndex = e.detail.current;
			}
		}
	}
</script>

<style>
	.topic-view {
		padding: 0 20rpx;
	}
</style>
