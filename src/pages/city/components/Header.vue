<template>
    <div>
        <div class="header">城市选择
            <router-link to="/">
                <div class="iconfont header-icon">&#xe611;</div>
            </router-link>
        </div>
        
    </div>
</template>
<script>
export default {
    name:"CityHeader"
}
</script>
<style lang="stylus" scoped>
@import '~@/assets/style/varibles.styl';
    .header{
        position relative
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



