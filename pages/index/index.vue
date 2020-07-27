<template>
	<view class="page">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item>
				<image src="../../static/carousel/batmanvssuperman.png" class="carousel"></image>
			</swiper-item>
			<swiper-item>
				<image src="../../static/carousel/spiderman.png" class="carousel"></image>
			</swiper-item>
			<!-- see 8.1 先学node服务 -->
		</swiper>
	</view>
</template>

<script>
	import common from '../../common/common.js'
	console.log(common)
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		// 页面加载
		onLoad() {
			let local = 
			common.serverUrl
			uni.request({
				url:local,
				method:'get',
				success:(res)=>{
					console.log(res)
				}
			})
		},
		methods: {
			
		}
	}
</script>

<style>
	@import url("./index.css");
</style>
