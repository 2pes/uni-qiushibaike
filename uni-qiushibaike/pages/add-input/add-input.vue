<template>
	<view>
		<uni-nav-bar left-icon="arrowleft" :statusBar="true" rightText="发布" @clickLeft="back" @clickRight="submit">
			<view class="nav-tab-bar u-f-ajc" @tap="changelook">
				{{yinsi}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<view class="uni-textarea">
			<!-- 多行输入 -->
			<textarea value="" v-model='text' placeholder="说一句话吧~"></textarea>
		</view>
		<!-- 多图 -->
		<upload-images @upload="upload"></upload-images>
		<!-- 弹出公告 -->
		<uni-popup :show="showpopup" position="middle" mode="fixed" @hidePopup="hidePopup">
			<view class="gonggao">
				<view class="u-f-ajc">
					<image src="../../static/common/addinput.png" mode="widthFix"></image>
				</view>
				<view>1.涉及黄色、政治、广告及骚扰信息</view>
				<view>2.涉及黄色、政治、广告及骚扰信息</view>
				<view>4.涉及黄色、政治、广告及骚扰信息</view>
				<button type="default" @tap="hidePopup">朕知道了</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	let changelook = ['所有人可见', '仅自己可见'];
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import uploadImages from "../../components/common/upload-images.vue";
	import uniPopup from "../../components/uni-popup/uni-popup.vue"
	export default {
		data() {
			return {
				yinsi: '所有人可见',
				text: '',
				imglist: [],
				// 弹出公告参数
				showpopup: true,
				isget: false
			}
		},
		components: {
			uniNavBar,
			uploadImages
		},
		onBackPress () {
			// 如果用户有输入值猜才保存
			if (!this.text && this.imglist.length < 1) { return; }
			if (!this.isget) {
				this.baocun();
				return true;
			}
			
		},
		methods: {
			baocun () {
				uni.showModal({
					content: '是否要保存为草稿？',
					canceltext: '不保存',
					sonfirmtext: '保存',
					success: (res) => {
						if (res.confirm) {
							console.log('保存');
						} else {
							console.log('不保存');
						}
						this.isget = true;
						uni.navigateBack({
							delta: 1
						})
					}
				});
			},
			back() {
				uni.navigateBack({
					delta: 1 //返回步数
				})
			},
			//隐私
			changelook() {
				uni.showActionSheet({
					itemList: changelook,
					success: (res) => {
						this.yinsi = changelook[res.tapIndex];
					}
				})
			},
			//发布
			submit() {

			},
			upload(arr) {
				this.imageList = arr;
			},
			hidePopup () {
				this.showpopup = false;
			},

		}
	}
</script>

<style lang="scss" scoped>
	.nav-tab-bar {
		width: 100%;
		margin-left: -20rpx;
		
	}
	uni-textarea {
		border: 1rpx solid #EEEEEE;
	}

	/* 公告 */
	.gonggao {
		width: 500rpx;

		image {
			width: 75%;
			margin-bottom: 20rpx;
		}

		button {
			background: #ffe934;
			color: #fff;
			margin-top: 20rpx;
		}
	}
</style>
