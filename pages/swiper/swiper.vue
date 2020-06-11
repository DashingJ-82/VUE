<template>
	<view class="content">
		<!-- 	<button type="primary" @click="click">api-tomcat</button> -->
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" class="swiper">
			<swiper-item v-for="item of list">
				<image :src="'http://localhost:8080/Twelve/'+item.src" class="img"></image>
			</swiper-item>
		</swiper>
		<!-- <swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" class="swiper">
			<swiper-item>
				<image src="http://localhost:8080/Twelve/1.jpg" class="img"></image>
			</swiper-item>
			<swiper-item>
				<image src="http://localhost:8080/Twelve/2.jpg" class="img"></image>
			</swiper-item>
			<swiper-item>
				<image src="http://localhost:8080/Twelve/3.jpg" class="img"></image>
			</swiper-item>	
		</swiper> -->
	</view>
</template>

<script>
	import show from '../../components/show.vue'
	export default {
		components: {
			show
		},
		data() {
			return {
				list: [] //存放图片地址
			}
		
		},
		onLoad() {
			this.getImageInfo()
		},
		methods: {
			// 调用数据库数据
			getImageInfo() {
				uni.request({
					url: "http://localhost:3001/js17080103",
					method: 'GET',
					success: (res) => {
						console.log(res)
						this.list = res.data
					}
				})
			}
		},
		created(){
			this.getImageInfo()
		}
	}
</script>

<style>
	.img{
			border-radius: 35%;
			border: 1px solid #55aaff;
		}
	.swiper{
			height:330px;
		}
</style>
