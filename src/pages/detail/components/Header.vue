<template>
	<div>
		<router-link tag="div" to="/" class="header-abs" v-show="showAbs">
			<i class="iconfont">&#xe622;</i>
		</router-link>
		<div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
			<router-link to="/">
				<div class="header-left">
					<i class="iconfont">&#xe622;</i>
				</div>
			</router-link>
			景点详情
		</div>
	</div>
</template>

<script>
	export default {
		name: 'DetailHeader',
		data () {
			return {
				showAbs: true,
				opacityStyle: {
					opacity: 0
				}
			}
		},
		methods: {
			handleScroll () {
				const top = document.documentElement.scrollTop
				if (top > 60) {
					let opacity = top / 140
					opacity = opacity > 1 ? 1 : opacity
					this.opacityStyle = { opacity }
					this.showAbs = false
				} else {
					this.showAbs = true
				}
			}
		},
		activated () {
			window.addEventListener('scroll', this.handleScroll)
		},
		deactived () {
			window.removeEventListener('scroll', this.handleScroll)
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~style/varibles.styl'
	.header-abs
		width:.76rem
		height:.76rem
		line-height:.76rem
		border-radius:50%
		background:rgba(0, 0, 0, .6)
		text-align:center		
		position:absolute
		top:.2rem
		left:.2rem
		color:#fff
	.header-fixed
		height: .86rem
		line-height: .86rem
		background: $bgColor
		color: #fff
		font-size: .32rem
		text-align:center
		position: fixed
		left:0
		top:0
		right:0
		z-index:2
		.header-left
			width:.64rem
			text-align:center
			color:#fff
			position: absolute
			left: 0
			top: 0
</style>