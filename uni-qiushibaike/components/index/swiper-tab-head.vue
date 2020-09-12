<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab">
			<block v-for="(tab ,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" :class="{'active':tabIndex==index}" @tap="tabtap(index)">{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props: {
			tabBars: Array,
			tabIndex: Number
		},
		methods: {
			tabtap(index) {
				this.$emit('tabtap', index);
			}
		}
	}
</script>

<style lang="scss" scoped>
	.uni-tab-bar {
		.uni-swiper-tab {
			border-bottom: 1rpx solid #EEEEEE;

			.swiper-tab-list {
				color: #969696;
				font-weight: bold;
			}

			.active {
				color: #343434;

				.swiper-tab-line {
					border-bottom: 6rpx solid #fede33;
					width: 70rpx;
					margin: auto;
					border-top: 6rpx solid #fede33;
					border-radius: 20rpx;
				}
			}
		}


	}
</style>
