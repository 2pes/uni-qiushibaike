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
				<swiper-item>
					<scroll-view scroll-y class="list">
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
	export default {
		components: {
			newsNavBar,
			commonList,
			loadMore
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


</style>
