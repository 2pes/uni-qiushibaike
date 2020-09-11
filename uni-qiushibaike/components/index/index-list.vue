<template>
	<view class="index-list animated fadeInLeft fast">
		<view class="index-list1 u-f-ac">
			<view class="u-f-ac">
				<image :src="item.userpic" lazy-load />
				{{item.username}}
			</view>
			<view class="u-f-ac conect" v-show="!isguanzhu" @tap="guanzhu">
				<view class="icon iconfont icon-yixiangkan"></view>关注
			</view>
		</view>
		<view class="index-list2" @tap="opendetail">{{item.title}}</view>
		<view class="index-list3 u-f-ajc" @tap="opendetail">
			<image :src="item.titlepic" mode="widthFix" lazy-load />>
			<template v-if="item.type ==='video'">
				<!-- 视频 -->
				<view class="index-list-play icon iconfont icon-xiami"></view>
				<view class="index-list-playinfo">{{item.playnum}}次播放{{item.long}}</view>
			</template>
		</view>
		<view class="index-list4 u-f-ac u-f-jsb">
			<view class="u-f-ac">
				<view class="u-f-ac" :class="{'active':(likeorno.index ==1)}" @tap="caozuo('ding')">
					<view class="icon iconfont icon-aixin"></view>
					{{likeorno.likenum}}
				</view>
				<view class="u-f-ac" :class="{'active':(likeorno.index ==2)}" @tap="caozuo('cai')">
					<view class="icon iconfont icon-buganxingqu"></view>
					{{likeorno.unlikenum}}
				</view>
			</view>
			<view class="u-f-ac">
				<view class="u-f-ac">
					<view class="icon iconfont icon-yingpingmoban"></view>
					{{item.commentnum}}
				</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-fenxiang"></view>
					{{item.sharenum}}
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		props: {
			item: Object,
			index: Number
		},
		data() {
			return {
				isguanzhu: this.item.isguanzhu,
				likeorno: this.item.likeorno
			};
		},
		methods: {
			// 点击关注事件
			guanzhu() {
				this.isguanzhu = true;
				uni.showToast({
					title: "关注成功"
				});
			},
			//  顶还是踩的操作
			caozuo(type) {
				switch (type) {
					case "ding":
						if (this.likeorno.index == 1) {
							return;
						}
						this.likeorno.likenum++;
						if (this.likeorno.index == 2) {
							this.likeorno.unlikenum--;
						}
						this.likeorno.index = 1;
						break;
					case "cai":
						if (this.likeorno.index == 2) {
							return;
						}
						this.likeorno.unlikenum++;
						if (this.likeorno.index == 1) {
							this.likeorno.likenum++;
						}
						this.likeorno.index = 2;
						break;
				}
			},
			// 进入详情页
			opendetail() {
				console.log("进入到详情页");
			}
		}
	};
</script>

<style scoped>
	.index-list {
		padding: 20upx;
		border-bottom: 1upx solid #eeeeee;
	}

	.index-list1 {
		justify-content: space-between;
	}

	.index-list1>view:first-child {
		color: #999999;
	}

	.index-list1>view:first-child image {
		width: 90upx;
		height: 90upx;
		border-radius: 50%;
		margin-right: 10upx;
	}

	.index-list1 .conect {
		radius: 5upx;
		padding: 0 10upx;
		background-color: #007aff;
	}

	.index-list2 {
		padding-top: 15upx;
		font-size: 32upx;
	}

	.index-list3 {
		padding-top: 15upx;
		position: relative;
	}

	.index-list3>image {
		width: 100%;
		border-radius: 20upx;
	}

	.index-list3 .index-list-play {
		position: absolute;
		font-size: 150upx;
		color: #ffffff;
	}

	.index-list3 .index-list-playinfo {
		position: absolute;
		right: 8upx;
		bottom: 8upx;
		background: rgba(51, 51, 51, 0.72);
		color: #ffffff;
		border-radius: 40upx;
		font-size: 22upx;
		padding: 0 12upx;
	}

	.index-list4 {
		padding: 15upx 0;
		justify-content: space-between;
	}

	.index-list4 view {
		color: #999999;
	}

	.index-list4>view>view:first-child {
		margin-right: 10upx;
	}

	.index-list4>view>view>view {
		margin-right: 10upx;
	}

	.index-list4 .active,
	.index-list4 .active>view {
		color: #c5f61c;
	}
</style>
