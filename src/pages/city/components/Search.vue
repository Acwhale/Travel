<template>
    <div>
        <div class="search">
            <input
             v-model="keyword" class="search-input" type="text" placeholder="输入城市名/拼音" />
        </div>
        <div class="search-content" ref="wrapper" v-show="keyword">
            <ul>
                <li class="search-item border-bottom" v-for="(item) of list" :key="item.id" 
                    @click="handleCityClick(item.name)">{{item.name}}</li>
                <li class="search-item border-bottom" v-show="hasNoData">暂无数据</li>
            </ul>
        </div>
    </div>
</template>
<script>
import BScroll from 'better-scroll'
import CityVue from '../City.vue';
export default {
    name:"CitySearch",
    props:{
        cities:Object
    },
    data(){
        return{
            keyword:'',
            list:[],
            timer:null,
        }
    },
    methods:{
        handleCityClick(city){
            // console.log(city);
            this.$store.dispatch('changeCity',city)
            this.$router.push('/')
        }
    },
    computed:{
        hasNoData(){
            return !this.list.length
        }
    },
    watch:{
        keyword(){
            if(this.timer){
                clearTimeout(this.timer)
            }
            if(!this.keyword){
                this.list = []
                return
            }
            this.timer = setTimeout(()=>{
                let result = []
                for(let i in this.cities){
                    this.cities[i].forEach(value => {
                        if(value.spell.indexOf(this.keyword)> -1 || value.name.indexOf(this.keyword) > -1){
                            result.push(value)
                        }
                    })
                }
                this.list = result
            },100)
        }
    },
    mounted(){
         this.scroll = new BScroll(this.$refs.wrapper)
    }
}   
</script>
<style lang="stylus" scoped>
    @import '~@/assets/style/varibles.styl'
    .search{
        position relative
        height .72rem
        background $bgColor
        padding .1rem
    }
    .search-input{
        box-sizing border-box
        padding .1rem
        height .62rem
        line-height .62rem
        width 98%
        text-align center
        border-radius .06rem
        color #666
        position absolute
        left: 1%; 
        top: 15%;
    }
    .search-content{
        z-index 1
        background #eee
        overflow hidden
        position absolute
        top 1.65rem
        left  0
        right 0
        bottom 0
    }
    .search-item{
        line-height .62rem
        color #666
        background #ffffff
        padding-left .2rem
    }
</style>
