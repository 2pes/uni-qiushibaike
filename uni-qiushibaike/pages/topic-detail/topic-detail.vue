<template>
	<view>
		<!-- 话题介绍 -->
		<topic-info :item="topicInfo"></topic-info>

		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollStyle="border-bottom:0;"
		 scrollItemStyle="width:50%;"></swiper-tab-head>
		<!-- 列表-->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tabList" :key="index">
				<template v-if="tabIndex==index">
					<!-- 列表-->
					<block v-for="(list,listIndex) in item.list" :key="listIndex">
						<common-list :item="list" :index="listIndex"></common-list>
					</block>
					<load-more :loadtext="item.loadtext"></load-more>
				</template>

			</block>
		</view>
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	import topicInfo from '../../components/topic/topic-info.vue'
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	import commonList from '../../components/common/common-list.vue';
	import loadMore from "../../components/common/load-more.vue";
	export default {
		components: {
			indexList,
			topicInfo,
			swiperTabHead,
			commonList,
			loadMore
		},
		data() {
			return {
				topicInfo: {
					title: '忆往事，敬余生',
					titlepic: '../../static/demo/topicpic/13.jpeg',
					desc: '话题描述话题描述话题描述话题描述',
					totalnum: 100,
					todaynum: 10
				},
				tabIndex: 0,
				tabBars: [{
						name: "默认",
						id: "moren"
					},
					{
						name: "最新",
						id: "zuixin"
					}
				],
				tabList: [{
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
				}, {
					loadtext: '上拉加载',
					list: [

						// 图文
						{
							userpic: '../../static/demo/datapic/1.jpg', // 头像
							username: '忆忘', // 昵称
							sex: 1, // 0 男 1 女
							age: 25, // 年龄
							isguanzhu: false, // 是否关注
							title: '黑夜的烟火,绚丽而短暂', // 标题
							titlepic: '../../static/demo/datapic/14.jpg', // 主题 图片
							video: false, // 主题 视屏
							share: false, // 主题 分享
							path: "深圳 龙岗", // 地址
							sharenum: 20, // 分享数量
							commentnum: 30, // 评论数
							goodnum: 20 // 点赞

						},
						// 视屏
						{
							userpic: '../../static/demo/datapic/1.jpg', // 头像
							username: '忆忘', // 昵称
							sex: 0, // 0 男 1 女
							age: 25, // 年龄
							isguanzhu: false, // 是否关注
							title: '黑夜的烟火,绚丽而短暂', // 标题
							titlepic: '../../static/demo/datapic/12.jpg', // 主题 图片
							video: {
								looknum: '20w',
								long: '2:20'
							}, // 主题 视屏
							share: false, // 主题 分享
							path: "深圳 龙岗", // 地址
							sharenum: 20, // 分享数量
							commentnum: 30, // 评论数
							goodnum: 20 // 点赞

						},
						{
							userpic: '../../static/demo/datapic/1.jpg', // 头像
							username: '忆忘', // 昵称
							sex: 1, // 0 男 1 女
							age: 25, // 年龄
							isguanzhu: false, // 是否关注
							title: '黑夜的烟火,绚丽而短暂', // 标题
							titlepic: '../../static/demo/datapic/12.jpg', // 主题 图片
							video: {
								looknum: '50w',
								long: '2:20'
							}, // 主题 视屏
							share: false, // 主题 分享
							path: "深圳 龙岗", // 地址
							sharenum: 20, // 分享数量
							commentnum: 30, // 评论数
							goodnum: 20 // 点赞

						},
						// 分享
						{
							userpic: '../../static/demo/datapic/1.jpg', // 头像
							username: '忆忘', // 昵称
							sex: 1, // 0 男 1 女
							age: 25, // 年龄
							isguanzhu: false, // 是否关注
							title: '黑夜的烟火,绚丽而短暂', // 标题
							titlepic: '', // 主题 图片
							video: false, // 主题 视屏
							share: {
								title: '远处只适合遥望......',
								titlepic: '../../static/demo/datapic/1.jpg'
							}, // 主题 分享
							path: "深圳 龙岗", // 地址
							sharenum: 20, // 分享数量
							commentnum: 30, // 评论数
							goodnum: 20 // 点赞

						},
						{
							userpic: '../../static/demo/datapic/1.jpg', // 头像
							username: '忆忘', // 昵称
							sex: 0, // 0 男 1 女
							age: 25, // 年龄
							isguanzhu: false, // 是否关注
							title: '黑夜的烟火,绚丽而短暂', // 标题
							titlepic: '', // 主题 图片
							video: false, // 主题 视屏
							share: {
								title: '远处只适合遥望......',
								titlepic: '../../static/demo/datapic/1.jpg'
							}, // 主题 分享
							path: "深圳 龙岗", // 地址
							sharenum: 20, // 分享数量
							commentnum: 30, // 评论数
							goodnum: 20 // 点赞

						}

					]
				}]



			}
		},
		//下拉刷新事件
		onPullDownRefresh() {
			this.getdata();
		},
		//上拉触底事案
		onReachBottom() {
			this.loadmore();
		},
		methods: {
			getdata() {

				setTimeout(() => {
					let arr = [{
						userpic: "../../static/demo/userpic/12.jpg", // 用户头像
						username: "hhh223123", // 用户昵称
						isguanzhu: true, // 是否关注
						sex: 1,
						age: 25,
						title: "我是标题123", // 标题
						video: {
							looknum: "20w",
							long: "2:33"
						},
						titlepic: "../../static/demo/datapic/12.jpg", // 标题图片
						share: false,
						path: "深圳 龙岗",
						commentnum: 0, // 评论
						sharenum: 11, // 转发（分享）
						goodnum: 10,

					}, {
						userpic: "../../static/demo/userpic/12.jpg", // 用户头像
						username: "hhh223123", // 用户昵称
						isguanzhu: true, // 是否关注
						sex: 1,
						age: 25,
						title: "我是标题123", // 标题
						video: {
							looknum: "20w",
							long: "2:33"
						},
						titlepic: "../../static/demo/datapic/12.jpg", // 标题图片
						share: false,
						path: "深圳 龙岗",
						commentnum: 0, // 评论
						sharenum: 11, // 转发（分享）
						goodnum: 10,

					}, {
						userpic: "../../static/demo/userpic/12.jpg", // 用户头像
						username: "hhh223123", // 用户昵称
						isguanzhu: true, // 是否关注
						sex: 1,
						age: 25,
						title: "我是标题123", // 标题
						video: {
							looknum: "20w",
							long: "2:33"
						},
						titlepic: "../../static/demo/datapic/12.jpg", // 标题图片
						share: false,
						path: "深圳 龙岗",
						commentnum: 0, // 评论
						sharenum: 11, // 转发（分享）
						goodnum: 10,

					}];
					this.tabList[this.tabIndex].list = arr;
					uni.stopPullDownRefresh()
				}, 2000)
			},
			loadmore() {
				// 上拉加载
				if (this.tabList[this.tabIndex].loadtext != '上拉加载更多') {
					return;
				}
				this.tabList[this.tabIndex].loadtext = "加载中...";
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
					this.tabList[this.tabIndex].list.push(obj);
					this.tabList[this.tabIndex].loadtext = "上拉加载更多";
				}, 1000)


				// this.guanzhu.loadtext = "没有更多数据了";

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

<style lang="scss" scoped>

</style>
