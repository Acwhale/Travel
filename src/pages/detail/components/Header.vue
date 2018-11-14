<template>
    <div>
        <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
            <div class="iconfont back-icon">&#xe611;</div>
        </router-link>
        <router-link to="/"  tag="div" class="header-fixed" v-show="!showAbs" :style="opacityStyle">
             <div class="iconfont header-icon">&#xe611;</div>
             景点详情
        </router-link>
    </div>
</template>
<script>
export default {
    name:"DetailHeader",
    data(){
        return {
            showAbs:true,
            opacityStyle:{
                opacity:0
            }
        }
    },
    methods:{
        handleScroll(){
            let top = document.documentElement.scrollTop
            if(top > 60){
                let opacity = top /140
                opacity = opacity > 1 ? 1 : opacity
                this.opacityStyle ={
                    opacity
                }
                this.showAbs = false
            }else{
                this.showAbs = true
            }
        }
    },
    activated(){
        window.addEventListener('scroll',this.handleScroll)
    },
    deactivated(){
        window.removeEventListener('scroll',this.handleScroll)
    }
}
</script>
<style lang="stylus" scoped>
 @import '~@/assets/style/varibles.styl';
    .header-abs{
        position absolute
        left .2rem
        top .2rem
        width .8rem
        height .8rem
        line-height .8rem
        text-align center
        border-radius .4rem
        background rgb(0,0,0,.8)
    }
    .back-icon{
        color  #fff
        font-size .4rem
    }
   
    .header-fixed{
        position fixed
        top 0 
        left 0 
        right  0
        overflow hidden
        height .86rem
        line-height  .86rem
        text-align center
        color #fff
        background $bgColor
        font-size .32rem
    }
    .header-icon{
        position absolute
        width .64rem
        text-align center
        font-size .4rem
        top 0
        left 0
        color #fff
    }
        
      
		
</style>
