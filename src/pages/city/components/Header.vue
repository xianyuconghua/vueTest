<template>
	<div class="header">
		<router-link to="/">
			<div class="header-left">
				<i class="iconfont">&#xe622;</i>
			</div>
		</router-link>
		城市选择
	</div>
</template>

<script>
	export default {
		name: 'CityHeader'
	}
</script>

<style lang="stylus" scoped="">
	@import '~style/varibles.styl'
	.header
		height: .86rem
		line-height: .86rem
		background: $bgColor
		color: #fff
		font-size: .32rem
		text-align:center
		position: relative
		.header-left
			width:.64rem
			text-align:center
			color:#fff
			position: absolute
			left: 0
			top: 0
</style>