<template>
	<view>
		<uni-nav-bar left-icon="arrowleft" :statusBar="true" rightText="发布" @clickLeft="back" @clickRight="submit">
			<view class="u-f-ajc" @tap="changelook">
				{{yinsi}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<view class="uni-textarea">
			<!-- 多行输入 -->
			<textarea value="" placeholder="说一句话吧~"></textarea>
		</view>
		<upload-images @upload="upload"></upload-images>
	</view>
</template>

<script>
	let changelook = ['所有人可见', '仅自己可见'];
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	import uploadImages from "../../components/common/upload-images.vue";
	export default {
		data() {
			return {
				yinsi: '所有人可见',
				text: "",
				imageList: []
			}
		},
		components: {
			uniNavBar,
			uploadImages
		},
		methods: {
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
			}

		}
	}
</script>

<style lang="scss" scoped>
	uni-textarea {
		border: 1rpx solid #EEEEEE;
	}
</style>
