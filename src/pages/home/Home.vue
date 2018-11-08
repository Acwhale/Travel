<template>
  <div>
		<home-header></home-header>
		<home-swiper :swiperList="swiperList"></home-swiper>
		<home-icons  :iconList="iconList"></home-icons>
		<home-recommend :recommendList="recommendList"></home-recommend>
		<home-weekend :weekendList="weekendList"></home-weekend>
	</div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
		HomeHeader,
		HomeSwiper,
		HomeIcons,
		HomeRecommend,
		HomeWeekend
  },
  data(){
	 return {
		swiperList:[],
		iconList:[],
		recommendList:[],
		weekendList:[],
		lastCity :'',
	 }
  },
  methods:{
	  //获取主页数据信息
	  getHomeInfo(){
		  axios.get('/api/index.json?city='+ this.$store.state.city)
		  	.then(this.getHomeInfoSucc)
	  },
	  getHomeInfoSucc(res){
		 console.log(res)
		 res = res.data
		 if(res.ret && res.data){
			this.swiperList = res.data.swiperList
			this.iconList = res.data.iconList
			this.recommendList = res.data.recommendList
			this.weekendList = res.data.weekendList
		 }
	  }
  },
  mounted(){
	  this.lastCity = this.$store.state.city
	  this.getHomeInfo()
  },
  activated(){
	// console.log(this.$store.state.city);
	if(this.lastCity !== this.$store.state.city){
		this.lastCity = this.$store.state.city
		this.getHomeInfo()
	}
  }
}
</script>

<style>
</style>
