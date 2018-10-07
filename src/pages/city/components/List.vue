<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">{{this.currentCity}}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
						<div class="button">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="area" v-for="(item, key) of cities" :key="key" :ref="key">
				<div class="title border-topbottom">{{key}}</div>
				<ul class="item-list">
					<li class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
	import Bscroll from 'better-scroll'
	import { mapState, mapMutations } from 'vuex'
	export default {
		name: 'CityList',
		props: {
			cities: Object,
			hot: Array,
			letter: String
		},
		computed: {
			...mapState({
				currentCity: 'city'
			})
		},	
		methods: {
			handleCityClick (city) {
				this.changeCity(city)
				this.$router.push('/')
			},
			...mapMutations(['changeCity'])
		},
		mounted () {
			this.scroll = new Bscroll(this.$refs.wrapper)
		},
		watch: {
			letter () {
				if(this.letter) {
					const element = this.$refs[this.letter][0]
					this.scroll.scrollToElement(element)
				}
			}
		}
	}
</script>

<style lang="stylus" scoped>
	.border-topbottom
		&:before
			border-color:#ddd
		&:after
			border-color:#ddd
	.border-bottom
		&:before
			border-color:#ddd
			
	.list
		position:absolute
		top:1.7rem
		left: 0
		right: 0
		bottom: 0
		overflow:hidden
		.title
			padding: .1rem .2rem
			background: #eee
			color:#666
			font-size: .24rem
		.button-list
			padding:.1rem .6rem .1rem .1rem
			overflow:hidden
			.button-wrapper
				width:33%			
				float: left
				.button
					padding:.1rem 0
					border: .02rem solid #ddd
					border-radius: .04rem
					text-align: center
					margin: .1rem
		.item
			padding: .2rem
			color: #666
</style>