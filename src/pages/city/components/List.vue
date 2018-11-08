<template>
    <div>
        <div class="list" ref="wrapper">
            <div >
                <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.$store.state.city}}</div>
                    </div>
                </div>
            </div>
                <div class="area">
                    <div class="title border-topbottom">热门城市</div>
                    <div class="button-list">
                        <div class="button-wrapper" v-for="item of hotCities" :key="item.id"> 
                            <div class="button" @click="handleCityClick(item.name)" >{{item.name}} </div>
                        </div>
                    </div>
                </div>
                <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
                    <div class="title ">{{key}}</div>
                    <div class="item-list" v-for="inner of item" :key="inner.id">
                        <div class="item border-bottom" @click="handleCityClick(inner.name)">{{inner.name}}</div>
                    </div>
            </div>
            </div>
        </div>
    </div>
</template>
<script>
import BScroll from 'better-scroll'
export default {
    Name:"CityList",
    props:{
        cities:Object,
        hotCities:Array,
        letter:String
    },
    mounted(){
        this.scroll = new BScroll(this.$refs.wrapper)
    },
    watch:{
        //监听letter是否变化了
        letter(){
            if(this.letter){
                let element = this.$refs[this.letter][0]
                // console.log(element)
                this.scroll.scrollToElement(element)
            }
            // console.log(this.letter)
        }
    },
    methods:{
        handleCityClick(city){
            this.$store.dispatch('changeCity',city)
            this.$router.push('/')
            // console.log(city)
        }
    }
}
</script>
<style lang="stylus" scoped>
    @import '~@/assets/style/varibles.styl'
    .list{
        overflow hidden
        position absolute
        top 1.58rem
        left 0
        right 0
        bottom 0
    }
    .title{
        line-height .44rem
        background #eee
        padding-left .2rem
        color #666
        font-size .26rem
        margin-top .1rem
    }
    .button-list{
        padding .1rem .6rem .1rem .1rem
        overflow hidden
    }
    .button-wrapper{
        float left
        width 33.33%
    }
    .button{
        text-align center
        margin .1rem
        border  .02rem solid #ccc
        padding .1rem 0
        border-radius .06rem
    }
    .item-list .item{
        line-height .76rem
        color #666
        padding .2rem
    }

</style>

