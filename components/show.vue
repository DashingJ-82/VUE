<template>
	<view>
		<view class="text">
			图片浏览：
		</view>
		<view>
			<!-- 拆分接收到的数组，图片展示 -->
			<image v-for="item of list" :src="'http://localhost/js17080103/'+item.src" mode="aspectFit" :key="item.id">
			</image>
		</view>
	</view>
</template>

<script>
	export default {
		// 父子传值
		props: ['list'],
		data() {
			return {

			}
		}
	}
</script>

<style>
	/* 文本样式 */
	.text {
		margin: 5px 0 15px 5px;
	}
</style>
