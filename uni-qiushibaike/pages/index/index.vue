<template>
	<view class="container">
		<block v-for="(item,index) in list" :key="index">
			<index-list :item="item" :index="index"></index-list>
		</block>
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	export default {
		components: {
			indexList
		},
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
		methods: {

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
