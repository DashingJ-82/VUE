<template>
    <view>
		 <view class="page-section page-section-gap" style="text-align: center;">
		                <audio style="text-align: left" :src="current.src" :poster="current.poster" :name="current.name" :author="current.author" :action="audioAction" controls></audio>
		</view>
		<view class="container"> 
		          <image class="bg-set" src="http://localhost:8080/Twelve/3.jpg"></image>
		</view> 
        <view class="uni-padding-wrap uni-common-mt">
            <view class="text-box" scroll-y="true">
                <text>{{text}}</text>
            </view>
            <view class="uni-btn-v">
                <button type="primary" :disabled="!canAdd" @click="add">add line</button>
                <button type="warn" :disabled="!canRemove" @click="remove">remove line</button>
            </view>
        </view>
    </view>
</template>
<script>
	export default {
	    data() {
	        return {
	            texts: [
	                '你曾是少年',
	                'S.H.E',
	                '有些时候 你怀念从前日子',
	                '可天真离开时 你却没说一个字',
	                '你只是挥一挥手 像扔掉废纸',
	                '说是人生必经的事',
	                '酒喝到七分 却又感觉怅然若失',
	                '镜子里面 像看到人生终点',
	                '或许再过上几年 你也有张虚伪的脸',
	                '难道我们 是为了这样 才来到这世上',
	                '这问题来不及想',
	                '每一天一年 总是匆匆忙忙',
	                '你我来自湖北四川广西宁夏河南山东贵州云南的小镇乡村',
					'曾经发誓 要做了不起的人',
					'却在北京上海广州深圳某天夜半忽然醒来 站在寂寞的阳台',
					'只想从这无边的寂寞中逃出来',
					'许多年前 你有一双清澈的双眼',
					'奔跑起来 像是一道春天的闪电',
					'想看遍这世界 去最遥远的远方',
					'感觉有双翅膀 能飞越高山和海洋'
	            ],
	            text: '',
	            canAdd: true,
	            canRemove: false,
	            extraLine: [],
				current: {
				                poster: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.jpg',
				                name: '你曾是少年',
				                author: 'S.H.E',
				                src: 'http://localhost:8080/Twelve/你曾是少年.mp3',
				            },
				            audioAction: {
				                method: 'pause'
				            }
	        }
	    },
	    methods: {
	        add: function(e) {
	            this.extraLine.push(this.texts[this.extraLine.length % 12]);
	            this.text = this.extraLine.join('\n');
	            this.canAdd = this.extraLine.length < 20;
	            this.canRemove = this.extraLine.length > 0;
	        },
	        remove: function(e) {
	            if (this.extraLine.length > 0) {
	                this.extraLine.pop();
	                this.text = this.extraLine.join('\n');
	                this.canAdd = this.extraLine.length < 12;
	                this.canRemove = this.extraLine.length > 0;
	            }
	        }
	    }
	}
</script>

<style>
	.bg-set{
	    position: fixed;
	    width: 80%;
	    height: 80%;
	    top: 5;
	    left: 0;
	    z-index: -1;
	}
</style>
