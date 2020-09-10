<template>
	<view class="container">
		<cu-custom bgColor="bg-gradual-blue" :isBack="true">
			<block slot="backText">返回</block>
			<block slot="content">导航栏</block>
		</cu-custom>
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
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: "www.baidu.com",
				PageCur: 'basics'
			}
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			}
		}
	}
</script>

<style>
	.container {
		/* padding: 20px; */
		font-size: 14px;
		line-height: 24px;
	}
</style>
