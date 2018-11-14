<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
            <swiper :options="swiperOption" >
                <!-- slides -->
                <swiper-slide v-for="(item,index) of imgs" :key="index">
                    <img class="swiper-image" :src="item" />
                </swiper-slide>

             <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
            <!-- <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div>
            <div class="swiper-scrollbar"   slot="scrollbar"></div> -->
            </swiper>
        </div>
    </div>
</template>
<script>
export default {
  name: "CommonGallary",
  props:{
      imgs:{
            type:Array,
            default(){
                return []
            }
      }
     
  },
  data(){
      return{
          swiperOption:{
                pagination:{
                    el:".swiper-pagination",
                    type:'fraction',
                    observeParents:true,
                    observe:true
                },
                
                loop:true
            },
      }
  },
  methods:{
      handleGallaryClick(){
          this.$emit("close")
      }
  }
};
</script>
<style lang="stylus" scoped>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        position: fixed;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        background: #000;
        z-index: 99;
    }

    .wrapper {
        width 100%;
        height 0;
        overflow hidden
        padding-bottom 100%
    }
    .swiper-pagination{
        color #fff
    }
   .swiper-image{
        width 100%
    }
</style>
