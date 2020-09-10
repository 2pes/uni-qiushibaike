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
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui'
			}
		},
		methods: {

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
