<template>
	<view class="content">
		<view>
			<ynGallery 
			 :galleryheight="165" 
			  bkstart="#000000" 
			  bkend="#000000" 
			 :imgviewwidth="85" 
			 :imgviewheight="105" 
			 :showbadge="true"
			  badegtype="trian" 
			  badegwidth="25" 
			  badegheight="25" 
			 :showdec="true" 
			 :images="testimgs" 
			 @clickimg="onclickimg">
			</ynGallery>
			<text style="font-size: 15px;">
				js17080103:{{Msg}}
			</text>
		</view>
		<view class="" style="background-color:white">
			<image class="logo" src="/static/logo.png"></image>
			<view>
				<text class="title">{{title}}</text>
			</view>
		</view>

	</view>
</template>


<script>
	import ynGallery from 'components/YnComponents/ynGallery/ynGallery.vue'

	export default {
		components: {
			ynGallery,
		},
		data() {
			return {
				sh: 0,
				Msg: "0",
				title: '拾贰',
				// 画廊示例数据
				testimgs: [{
						url: "http://localhost:8080/Twelve/1.jpg"
					},
					{
						url: "http://localhost:8080/Twelve/2.jpg"
					},
					{
						url: "http://localhost:8080/Twelve/3.jpg"
					},
					{
						url: "http://localhost:8080/Twelve/4.jpg"
					},
					{
						url: "http://localhost:8080/Twelve/5.jpg"
					},
					{
						url: "http://localhost:8080/Twelve/6.jpg"
					}
				],
			}
		},
		
		
		onLoad(){
			this.setimgs();
		},
    

		methods: {
			onclickimg(imgviewobj) {
				if (imgviewobj.index != undefined)
					this.Msg = `${imgviewobj.index}`;
			},
			setimgs() {
				var imgs=[];
				for (let i in this.testimgs) {									
					 let imgobj={
						  dec:'',                   //图像描述信息
						  badeg:'',                 //角标文字
						  badegcolor:'#000000',     //角标颜色
						  url:'',                   //图源  
						  dominant:''               //主色  
					};
					imgobj.url=this.testimgs[i].url;
					imgobj.dominant = this.retcolor(); //随机主色
					imgobj.dec = i; //描述  
					imgobj.badeg = i; //角标文字
					imgobj.badegcolor = (i % 2) == 0 ? 'red' : 'LimeGreen'; //角标颜色
					
					imgs.push(imgobj)
				}
				this.testimgs=imgs;
			},
			retcolor() {
				let color = '#' + ('00000' + (Math.random() * 0x1000000 << 0).toString(16)).substr(-6);
				return color;
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 100upx;
		width: 100upx;
		margin-top: 350upx;
		margin-bottom: 10upx;
		border-radius: 50upx;
	}

	.title {
		font-size: 72upx;
		color: #8f8f94;
	}
</style>
