<template>
	<div>
		<div class="banner" @click="handleBannerClick">
			<img class="banner-img" :src="bannerImg">
			<div class="banner-info">
				<div class="banner-title">{{this.sightName}}</div>
				<div class="banner-number">
					<i class="iconfont">&#xe663;</i>
					{{this.gallaryImgs.length}}
				</div>
			</div>
		</div>
		<common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
	</div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
	export default {
		name: 'DetailBanner',
		props: {
			sightName: String,
			bannerImg: String,
			gallaryImgs: Array
		},
		data () {
			return {
				showGallary:false
			}
		},
		methods: {
			handleBannerClick () {
				this.showGallary = true
			},
			handleGallaryClose () {
				this.showGallary = false
			}
		},
		components: {
			CommonGallary
		}
	}
</script>

<style lang="stylus" scoped>
	.banner
		overflow:hidden
		height:0
		padding-bottom:55%
		position:relative
		.banner-img
			width:100%
		.banner-info
			display:flex
			position:absolute
			left:0
			right:0
			bottom:0
			color:#fff
			line-height:.8rem
			background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, .8))
			.banner-title
				flex:1
				font-size: .36rem
				padding:0 .2rem
			.banner-number
				height:.4rem
				line-height:.4rem
				padding:0 .4rem
				border-radius:.2rem
				background:rgba(0, 0, 0, .6)
				margin:.2rem .2rem 0 0
				font-size:.32rem
</style>