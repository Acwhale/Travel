<template>
   <div class="wrapper">
    <swiper :options="swiperOption" >
    <!-- slides -->
    <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-image" :src="item.imgUrl" />
    </swiper-slide>

    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
    <!-- <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div>
    <div class="swiper-scrollbar"   slot="scrollbar"></div> -->
    </swiper>
   </div>
</template>
<script>
export default {
    name:'HomeSwiper',
    props:{
        swiperList:Array,
    },
    data(){
        return{
            swiperOption:{
                pagination:{
                    el:".swiper-pagination",
                },
                loop:true
            },
        }
    }
}
</script>
<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active{
         background #fff !important
    }
    .wrapper{
        overflow hidden
        width 100%
        height 0
        padding-bottom 28.5%
    }
    .swiper-image{
        width 100%
    }
</style>
