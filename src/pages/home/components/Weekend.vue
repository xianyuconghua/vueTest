<template>
	<div>
		<div class="title">周末去哪儿</div>
		<ul>
			<li class="weekend" v-for="item of list" :key="item.id">
				<div class="weekend-img">
					<img :src="item.imgUrl">
				</div>
				<div class="weekend-info">
					<p class="weekend-title">{{item.title}}</p>
					<p class="weekend-desc">{{item.desc}}</p>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'HomeWeekend',
		props: {
			list: Array
		}
		
	}
</script>

<style lang="stylus" scoped>
	@import '~style/mixins.styl'
	.title
		padding:.2rem
		background:#eee
	.weekend
		margin-bottom:.1rem
		.weekend-img
			height:0
			padding-bottom:37.3%
			overflow:hidden
		.weekend-img img
			width:100%
		.weekend-info
			padding:.1rem .2rem
			.weekend-title
				font-size:.28rem
				line-height:.4rem
			.weekend-desc
				line-height:.4rem
				color:#999
				ellipsis()
		
</style>