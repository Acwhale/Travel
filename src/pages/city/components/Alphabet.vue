<template>
    <div>
        <ul class="list">
            <li class="item" v-for="(item) of letters" :key="item"
            :ref="item"
            @click="handleLetterClick" @touchstart="handleTouchStart"
                                       @touchmove="handleTouchMove"
                                       @touchend="handleTouchEnd">{{item}}</li>
        </ul>
    </div>
</template>
<script>
export default {
    name:"CityAlphabet",
    
    props:{
        cities:Object
    },
    
    data(){
        return{
            touchStatus:false,
            startY:0,
            timer:null
        }
    },
    computed:{
        letters(){
            let letters = []
            for(let i in this.cities){
                letters.push(i)
            }
            return letters
        }
    },

    methods:{
        //向外触发事件
        handleLetterClick:function(e){
            // console.log(e.target.innerText)
            this.$emit("change",e.target.innerText)
        },

        handleTouchStart(){
            this.touchStatus = true
        },
        handleTouchMove(e){
            if(this.touchStatus){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                this.timer = setTimeout(()=>{
                    // let startY = this.$refs['A'][0].offsetTop
                    let touchY = e.touches[0].clientY-79
                    let index = Math.floor((touchY - this.startY) / 25)
                    // console.log(index)
                    if(index >= 0 && index < this.letters.length){
                        this.$emit("change",this.letters[index])
                    }
                },16)
                
                
            }
        },
        handleTouchEnd(){
            this.touchStatus = false
        }
    },
    updated(){
        this.startY = this.$refs['A'][0].offsetTop
    }
}
</script>
<style lang="stylus" scoped>
    @import '~@/assets/style/varibles.styl'
    .list{
        display flex 
        flex-direction column
        justify-content center
        position absolute
        top 1.68rem
        right 0
        bottom 0
        width  .4rem
        
    }
    .item{
        text-align  center
        height .76rem
        line-height .44rem
        color $bgColor
    }

</style>

