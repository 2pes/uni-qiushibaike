<template>
	<view class="container">
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newsList" :key="index">
					<scroll-view scroll-y class="list">
						<block v-for="(item,index1) in items.list" :key="index1">
							<index-list :item="item" :index="index1"></index-list>
						</block>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	export default {
		components: {
			indexList,
			swiperTabHead
		},
		data() {
			return {
				swiperHeight: 500,
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "1",
						num:10
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
						type: "video", // img: 图文， video: 视频
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
				}, {
					list: [{

						userpic: "../../static/demo/userpic/11.jpg", // 用户头像
						username: "昵称2", // 用户昵称
						isguanzhu: true, // 是否关注
						title: "我是标题", // 标题
						type: "video", // img: 图文， video: 视频
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
				}, {
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

					}]
				}],
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
					type: "video", // img: 图文， video: 视频
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
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight;
					this.swiperHeight = height;
				}
			})
		},
		methods: {
			tabtap(index) {
				this.tabIndex = index;
			},
			tabChange(e) {
				this.tabIndex = e.detail.current;
			}
		}

	}
</script>

<style lang="scss">
	.container {
		/* padding: 20px; */
		font-size: 14px;
		line-height: 24px;


	}
</style>
