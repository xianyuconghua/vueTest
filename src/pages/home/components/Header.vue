<template>
	<div class="header">
		<div class="header-left">
			<i class="iconfont">&#xe622;</i>
		</div>
		<div class="header-input">
			<i class="iconfont">&#xe663;</i>
			输入城市/景点/游玩主题
		</div>
		<router-link to="/city">
			<div class="header-right">
				{{this.city}}
				<i class="iconfont">&#xe615;</i>
			</div>
		</router-link>
	</div>
</template>

<script>
import { mapState } from 'vuex'
	export default {
		name: 'HomeHeader',
		computed: {
			...mapState(['city'])
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~style/varibles.styl'
	.header
		display:flex
		line-height:.86rem
		background:$bgColor
		color:#fff
		.header-left
			width:.64rem
			text-align:center
		.header-input
			flex:1
			height:.64rem
			line-height:.64rem
			background:#fff
			border-radius:.08rem
			margin-top:.1rem
			color:#ccc
			padding: 0 .2rem
			box-sizing:border-box
		.header-right
			min-width:1.04rem
			padding: 0 .2rem 0 .1rem
			text-align:center
			color:#fff
</style>