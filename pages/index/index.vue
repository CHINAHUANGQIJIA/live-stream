<template>
	<view class="container">
		<view class="intro">本项目已包含uni ui组件，无需import和注册，可直接使用。在代码区键入字母u，即可通过代码助手列出所有可用组件。光标置于组件名称处按F1，即可查看组件文档。</view>
		<text class="intro">详见：</text>
		<uni-link :href="href" :text="href"></uni-link>
	</view>
</template>

<script>
	export default {
		data() {
			return {};
		},
		//uni生命周期函数，页面显示就执行，这意味着如果一打开这个页面，如果没登录将永远跳转到登录页面
		onShow() {
			/****************************************************用户是否登录代码开始:https://www.clearnull.com/963.html*****/
			//uni获取本地数据API
			uni.getStorage({
				key: 'token', //数据key值，也就是你存储数据时的名称
				success: function(res) {
					//数据成功获取，用户已登录
					console.log(res.data);
				},
				fail: function(res) {
					//数据未获取成功，用户没有登录，这里我们直接跳转到登录页面
					uni.navigateTo({
						url: '../login/login',
					});
				}
			});
			/*************************************用户是否登录代码结束**********************/
		}
	};
</script>

<style>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}
</style>
