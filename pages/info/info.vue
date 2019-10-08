<template>
	<view class="zong">
		<view class="title">
			{{title}}
		</view>
		<view class="content">
			<rich-text class="richText" :nodes="content"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title : '',
				content : ''
			}
		},
		onLoad:function(e){
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+ e.postid,
				method: 'GET',
				data: {},
				success: res => {
					// console.log(res.data.post_id);
					console.log(res);
					this.title = res.data.title;
					this.content = res.data.content;
				},
				fail: () => {},
				complete: () => {}
			});
		}
	}
</script>

<style>
.zong{padding: 10rpx 2%; width: 96%; flex-wrap: wrap;}
.title{line-height: 2em; font-weight: 700; font-size: 38rpx;}
.content{line-height: 2em;}
</style>
