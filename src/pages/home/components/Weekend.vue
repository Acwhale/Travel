<template>
    <div>
        <div class="weekend-title">周末游</div>
        <div class="weekend-container" v-for=" item of weekendList" :key="item.id">
            <img class="item-img" :src="item.imgUrl"/>
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"HomeWeekend",
    data(){
        return{
            weekendList:[
                {
                    id:'001',
                    imgUrl:"http://img1.qunarzz.com/sight/source/1509/d4/fc8b971f328b79.jpg_r_640x214_d161f3ff.jpg",
                    title:"太原周边赏秋",
                    desc:"秋风送爽，赏秋图绘制美丽新太原"
                },
                {
                    id:'003',
                    imgUrl:"http://img1.qunarzz.com/sight/source/1509/d4/fc8b971f328b79.jpg_r_640x214_d161f3ff.jpg",
                    title:"太原周边赏秋",
                    desc:"秋风送爽，赏秋图绘制美丽新太原"
                },
                {
                    id:'002',
                    imgUrl:"http://img1.qunarzz.com/sight/source/1509/d4/fc8b971f328b79.jpg_r_640x214_d161f3ff.jpg",
                    title:"太原周边赏秋",
                    desc:"秋风送爽，赏秋图绘制美丽新太原"
                }
            ]
        }
    }
}
</script>
<style lang="stylus" scoped>
    .weekend-title{
        margin-top .2rem
        line-height .8rem
        background #eeeeee
        text-indent .2rem
    }
    .weekend-container{
        display flex
        flex-direction column
        align-items flex-start
        width 100%
    }
    .item-img{
        width 100%
        height 33.9%
    }
    .item-info{
        padding .1rem
    }
    .item-title{
        line-height .54rem
        font-size .32rem
        ellipsis()
    }
    .item-desc{
        line-height .4rem
        color #ccc
    }
</style>
