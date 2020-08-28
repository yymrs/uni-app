<template>
	<view class="page">
		<!-- 轮播 -->
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="item in img_arr">
				<image :src="item.img_url" class="carousel"></image>
			</swiper-item>
		</swiper>
		<!-- 热门电影 -->
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/hot.png" class="hot-ico"></image>
				<view class="hot-title">
					热门影视 
				</view>
			</view>
		</view>
		<scroll-view class="page-block hot" scroll-x="true"  scroll-left="120">
			<view class="single-poster" v-for="item in hot_arr">
				<view class="poster-wapper">
					<image :src="item.cover" class="poster"></image>
					<view class="movie-name">
						{{item.name}}
					</view>
					<trailerstars :showNum='item.score'></trailerstars>
				</view>
			</view>
		</scroll-view>
		<view class="page-block super-hot">
			<view class="hot-title-wapper">
				<image src="../../static/icos/interest.png" class="hot-ico"></image>
				<view class="hot-title">
					热门预告 
				</view>
			</view>
		</view>
		<view class="hot-movies page-block">
			<video 
			class="hot-movie-single"
			v-for="video in trailer"
			:src="video.trailer" 
			:poster="video.poster"
			controls></video>
		</view>
	</view>
</template>

<script>
	import common from '../../common/common.js'
	import trailerstars from '../../components/trailerstars.vue'
	console.log(common)
	export default {
		data() {
			return {
				title: 'Hello',
				img_arr: [],
				hot_arr:[],
				trailer:[]
			}
		},
		// 页面加载
		onLoad() {
			let local = common.serverUrl
			uni.request({
				url: `${local}/api/index/imgulr`,
				method: 'get',
				success: (res) => {
					console.log(res)
					this.img_arr = res.data
				},
				fail(res) {
					console.log(res);
				},
				complete() {
					console.log('成功失败都执行');
				}
			})
			// http://www.imovietrailer.com:909/#/          线上地址
			uni.request({
				url:'https://www.imovietrailer.com/superhero/search/list?qq=lee33331070&keywords=&page=&pageSize=',
				method:'POST',
				success:(res)=> {
					this.hot_arr = res.data.data.rows
				}
			})
			uni.request({
				url:'https://www.imovietrailer.com/superhero/index/movie/hot?type=trailer&qq=lee33331070',
				method:'POST',
				success:(res)=> {
					console.log(res);
					this.trailer = res.data.data
				}
			})
		},
		methods: {

		},
		components:{
			trailerstars,
		}
	}
</script>

<style>
	@import url("./index.css");
</style>
