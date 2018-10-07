<template>
	<div class="icons">
		<swiper :options="swiperOption">
			<swiper-slide v-for="(page, index) of pages" :key="index">
				<div class="icon" v-for="item of page" :key="item.id">
					<div class="icon-content">
						<img class="icon-img" :src="item.imgUrl">
					</div>
					<p class="icon-desc">{{item.desc}}</p>
				</div>
			</swiper-slide>
			<div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>

<script>
	export default {
		name: 'HomeIcons',
		props: {
			list: Array
		},
		data () {
			return {
				swiperOption: {
					pagination:'.swiper-pagination'
				}
			}
			
		},
		computed: {
			pages () {
				const pages = []
				this.list.forEach((item, index) => {
					const page = Math.floor(index / 8)
					if(!pages[page]){
						pages[page] = []
					}
					pages[page].push(item)
				})
				return pages
			}
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~style/mixins.styl'
	.icons >>> .swiper-container
		width:100%
		height:0
		padding-bottom:58%
	.icon
		overflow:hidden
		float:left
		width:25%
		height:0
		padding-bottom:25%
		position:relative
		.icon-content
			position:absolute
			top:0
			left:0
			right:0
			bottom:.48rem
			text-align:center
			padding:.06rem 0 
			box-sizing:border-box
			.icon-img
				height:100%
				margin-top:.2rem		
		.icon-desc
			position:absolute
			left:0
			right:0
			bottom:0
			height:.44rem
			line-height:.48rem
			text-align:center
			ellipsis()
</style>