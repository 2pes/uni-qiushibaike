<template>
	<view>
		<uni-nav-bar left-icon="arrowleft" :statusBar="true" rightText="发布" @clickLeft="back" @clickRight="submit">
			<view class="u-f-ajc" @tap="changelook">
				{{yinsi}}
				<view class="icon iconfont icon-zhibo"></view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
	let changelook = ['所有人可见', '仅自己可见'];
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";
	export default {
		data() {
			return {
				yinsi: '所有人可见'
			}
		},
		components: {
			uniNavBar
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

			}
		}
	}
</script>

<style>

</style>
