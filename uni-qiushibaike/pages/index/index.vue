<template>
	<view class="container">
		<!-- 	<cu-custom bgColor="bg-gradual-blue">
			<block slot="backText">返回</block>
			<block slot="content">导航栏</block>
		</cu-custom> -->
		<!-- <view class="cu-bar search bg-white">
			<view class="cu-avatar round" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big11010.jpg"></view>
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input @focus="InputFocus" @blur="InputBlur" :adjust-position="false" type="text" placeholder="搜索图片、文章、视频" confirm-type="search"></input>
			</view>
			<view class="action">
				<text>广州</text>
				<text class="cuIcon-triangledownfill"></text>
			</view>
		</view>
		<view class="intro">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<text class="intro">详见：</text>
		<uni-link :href="href" :text="href"></uni-link>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-navigate uni-navigate-right">
					例子
				</view>
			</view>
		</view>
		<view class="uni-list">
			<view class="uni-list-cell">
				<view class="uni-list-cell-navigate uni-navigate-right">
					例子
				</view>
			</view>
		</view>
		<view>
			<navigator url="../ceshi/ceshi" hover-class="navigator-hover">
				<button type="default">跳转到新页面</button>
			</navigator>
		</view>


		<view class="cu-bar tabbar bg-white shadow foot">
			<view class="action" @click="NavChange" data-cur="basics">
				<view class="cuIcon-cu-image">
					<image src="/static/tabbar/basics_cur.png"></image>
				</view>
				<view class="text-green">元素</view>
			</view>
			<view class="action" @click="NavChange" data-cur="basics">
				<view class="cuIcon-cu-image">
					<image src="/static/tabbar/component.png"></image>
				</view>
				<view class="text-gray">组件</view>
			</view>
			<view class="action" @click="NavChange" data-cur="component">
				<view class="cuIcon-cu-image">
					<image src="/static/tabbar/plugin.png"></image>
					<view class="cu-tag badge">99</view>
				</view>
				<view class="text-gray">扩展</view>
			</view>
			<view class="action" @click="NavChange" data-cur="component">
				<view class="cuIcon-cu-image">
					<image src="/static/tabbar/about.png"></image>
					<view class="cu-tag badge"></view>
				</view>
				<view class="text-gray">关于</view>
			</view>
		</view> -->
		<view class="index-list">
			<view class="index-list1 u-f-ac u-f-jsb">
				<view class="u-f-ac">
					<image src="../../static/demo/userpic/12.jpg" mode="widthFix" lazy-load></image>昵称
				</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
			</view>
			<view class="index-list2">我是标题</view>
			<view class="index-list3">
				<image src="../../static/demo/datapic/11.jpg" mode="widthFix" lazy-load></image>
			</view>
			<view class="index-list4 u-f-ac u-f-jsb">
				<view class="u-f-ac">
					<view class="u-f-ac">
						<view class="icon iconfont icon-icon_xiaolian-mian"></view>20

					</view>
					<view class="u-f-ac">
						<view class="icon iconfont icon-kulian"></view>20
					</view>
				</view>
				<view class="u-f-ac">
					<view class="u-f-ac">
						<view class="icon iconfont icon-pinglun"></view>20

					</view>
					<view class="u-f-ac">
						<view class="icon iconfont icon-zhuanfa"></view>10
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {}
		},
		methods: {

		}

	}
</script>

<style lang="scss">
	.u-f,
	.u-f-ac,
	.u-f-ajc {
		display: flex;
	}

	.u-f-ac,
	.u-f-ajc {
		align-items: center;
	}

	.u-f-ajc {
		justify-content: center;
	}

	.u-f-jsb {
		justify-content: space-between;
	}

	.container {
		/* padding: 20px; */
		font-size: 14px;
		line-height: 24px;

		.index-list {
			padding: 20rpx;
			border-bottom: 1rpx solid #EEEEEE;
		}

		.index-list1 {
			view:first-child {
				color: #999999;
			}
			view:first-child image {
				width: 90rpx;
				height: 90rpx;
				border-radius: 100%;
				margin-right: 10rpx;
			}
			view:last-child {
				background: #F4F4F4;
				border-radius: 2rpx;
				padding: 0 10rpx;
			}
		}

		.index-list2 {
			padding-top: 15rpx;
			font-size: 32rpx;
		}

		.index-list3 {
			padding-top: 15rpx;
			image {
				width: 100%;
				border-radius: 20rpx;
			}
		}

		.index-list4 {
			padding: 15rpx 0;
			view {
				color: #999999;

				view {


					view,
					view:first-child {
						margin-right: 10rpx;
					}


				}
			}
		}
	}
</style>
