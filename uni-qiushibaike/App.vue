<script>
	export default {
		onLaunch: function() {
			console.log('App Launch');
		},
		onShow: function() {
			console.log('App Show');
		},
		onHide: function() {
			console.log('App Hide');
		}
	};
	// http://47.52.168.156:8888/
	//ceshi2.dishait.cn/
	/* export default {
	// api请求前缀
	webUrl:'https://ceshi2.dishait.cn/api/v1',
	// websocket地址
	websocketUrl:"wss://ceshi2.dishait.cn/wss",
} */
</script>

<style>
	/*每个页面公共css */
	@import './common/uni.css';
	/* 引用第三方图表库--阿里 */
	@import './common/iconfont.css';
	/* @import url("https://at.alicdn.com/t/font_1663690_krhhk9r8qua.css"); */
	/* 引用第三方动画库--animate.css */
	@import './common/animate.css';
	@import './common/common.css';

	/* 解决头条小程序组件内引入字体不生效的问题 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		src: url('/static/uni.ttf');
	}

	/* #endif */
</style>
