<template name='trailerstars'>
	<view class="movie-score-wapper">
		<!-- <image src="../static/icos/star-yellow.png" class="star-ico"></image>
		<image src="../static/icos/star-yellow.png" class="star-ico"></image>
		<image src="../static/icos/star-yellow.png" class="star-ico"></image>
		<image src="../static/icos/star-yellow.png" class="star-ico"></image> -->
		<image v-for="num in yellowScore" src="../static/icos/star-yellow.png" class="star-ico"></image> 
		<image v-for="num in grayScore" src="../static/icos/star-gray.png" class="star-ico"></image>
		<view class="movie-score" v-if="showNum">
			{{showNum}}
		</view>

	</view>
</template>

<script>
	export default {
		name: 'trailerstars',
		props:{
			innerScore:0,
			showNum:0
		},
		data() {
			return {
				yellowScore:0,
				grayScore:5
			};
		},
		onLoad() {
			console.log('load');
		},
		created() {
			console.log(Math.floor(this.showNum/2));
			
			this.yellowScore = Math.floor(this.showNum/2)
			this.grayScore = this.grayScore - this.yellowScore 
		}
	}
</script>

<style lang="scss">
.movie-score-wapper {
	display: flex;
	flex-direction: row;
}
.star-ico  {
	width: 20upx;
	height: 20upx;
	margin-top: 6upx;
}
.movie-score {
	font-weight: bold;
	color: grey;
	margin-left: 8upx;
	font-size: 12upx
}
</style>
