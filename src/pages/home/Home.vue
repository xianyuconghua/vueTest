<template>
	<div>
		<home-header></home-header>
		<home-swiper :list="swiperList"></home-swiper>
		<home-icons :list="iconList"></home-icons>
		<home-like :list="likeList"></home-like>
		<home-weekend :list="weekendList"></home-weekend>
	</div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeLike from './components/Like'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
	name: 'Home',
	components: {
		HomeHeader,
		HomeSwiper,
		HomeIcons,
		HomeLike,
		HomeWeekend
	},
	data () {
		return {
			lastCity: '',
			swiperList: [],
			iconList: [],
			likeList: [],
			weekendList: []
		}
	},
	computed: {
		...mapState(['city'])
	},
	methods: {
		getHomeInfo () {
			axios.get('/api/index.json?city=' + this.city)
			.then(this.getHomeInfoSucc)
		},
		getHomeInfoSucc (res) {
			res = res.data
			if(res.ret && res.data) {
				const data = res.data
				this.swiperList = data.swiperList
				this.iconList = data.iconList
				this.likeList = data.likeList
				this.weekendList = data.weekendList
			}
			// console.log(res)
		}
	},
	mounted () {
		this.lastCity = this.city
		this.getHomeInfo()
	},
	activated () {
		if (this.lastCity !== this.city) {
			this.lastCity = this.city
			this.getHomeInfo()
		}
	}
}
</script>

<style lang="stylus" scoped>

</style>