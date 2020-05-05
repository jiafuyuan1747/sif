<template>
	<view class="content">
		<head-one></head-one>
		<head-one></head-one>
		<head-one></head-one>
		<head-one></head-one>
		<head-one></head-one>
<!--		<view>-->
<!--			<text class="title">{{title}}</text>-->
<!--		</view>-->
	</view>
</template>

<script>
	import headOne from "../../components/headOne";
	export default {
		components: {
			headOne //第二步，注册组件
		},
		data() {
			return {
				title: '陆巡你没有马'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss">
	.content {
		text-align: center;
		display: flex;
		flex-wrap: wrap;
	}
	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
