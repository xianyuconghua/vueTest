<template>
	<div>
		<div class="title">猜你喜欢</div>
		<ul>
			<router-link 
				tag="li" 
				class="like border-bottom" 
				v-for="item of list" 
				:key="item.id" 
				:to="'/detail/' + item.id"
			>
				<div class="like-img">
					<img :src="item.imgUrl">
				</div>
				<div class="like-info">
					<p class="like-title">{{item.title}}</p>
					<p class="like-desc">{{item.desc}}</p>
					<button class="like-button">查看详情</button>
				</div>
			</router-link>
		</ul>
	</div>
</template>

<script>
	export default {
		name: 'HomeLike',
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
	.like
		display:flex
		padding:.2rem
		.like-img
			width:2rem
			height:2rem
			overflow:hidden
		.like-img img
			width:100%
		.like-info
			flex:1
			margin-left:.2rem
			min-width:0
			.like-title
				font-size:.32rem
				line-height:.6rem
				ellipsis()
			.like-desc
				line-height:.4rem
				color:#999
				ellipsis()
			.like-button
				padding:0 .2rem .06rem
				background:#ff9300
				color:#fff
				font-size:.24rem
				border-radius:.06rem
				margin-top:.2rem
		
</style>