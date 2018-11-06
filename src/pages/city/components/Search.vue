<template>
    <div>
        <div class="search">
            <input class="search-input" type="text" placeholder="输入城市名/拼音" />
        </div>
    </div>
</template>
<script>
export default {
    name:"CitySearch"
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
</style>
