<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img  class="banner-img" :src="bannerImgs" />
            <div class="banner-info">
                <div class="banner-title">
                        111111
                </div>
                <div class="banner-number">
                    <span class="iconfont">&#xe605;</span> 39
                </div>
            </div>
            </div>
        <common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="hanleGallaryClose"></common-gallary>
    </div>
</template>

<script>
import CommonGallary from '@/common/gallary/Gallary'
import axios from 'axios'
export default {
    name: 'DetailBanner',
    components:{
        CommonGallary
    },
    data(){
        return{
            bannerImgs:[],
            gallaryImgs:[],
            showGallary:false
        }
    },
    methods:{
       getBannerInfo(){
           axios.get('/api/detail.json').then((res)=>{
               console.log(res)
               res = res.data
               if(res.ret && res.data){
                   this.gallaryImgs = res.data.gallaryImgs
                   this.bannerImgs = res.data.bannerImg
               }
           })
       },
       handleBannerClick(){
            this.showGallary = true
        },
        hanleGallaryClose(){
            this.showGallary = false
        }
    },
 
    mounted(){
        this.getBannerInfo()
    }
}
</script>
<style lang='stylus' scoped>
    .banner 
        position relative
        overflow hidden
        height 0
        padding-bottom 55%
        .banner-img
            width 100%
        .banner-info
            width 100%
            background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
            display flex
            color #fff
            position absolute
            align-items baseline
            line-height .6rem
            right 0
            left 0
            bottom 0
            .banner-title
                padding 0 .2rem
                font-size .32rem
                flex 1 
            .banner-number
                background rgba(0,0,0,0.8)
                height .4rem
                line-height .4rem
                padding 0 .4rem
                border-radius .4rem
</style>
