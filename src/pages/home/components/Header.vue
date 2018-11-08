<template>
    <div class="header-container">
        <div class="header-left">
			<div class="iconfont back-icon">&#xe611;</div>
		</div>
        <div class="header-input">
			<span class="iconfont">&#xe603;</span>
					 输入城市/景点/游玩主题
		</div>
        <router-link to="/city">
			<div class="header-right">
				{{this.$store.state.city}}
				<span class="iconfont arrow-left">&#xe656;</span>
			</div>
		</router-link>
    </div>
</template>
<script>

export default {
  name: 'HomeHeader',
  props:{
	  city:String
  }
}
</script>
<style lang="stylus" scoped>
@import '~@/assets/style/varibles.styl';
    .header-container{
				width 100%;
        		display  flex
        		flex-direction : row
        		align-items center
        		line-height  .86rem
				justify-content  space-between
				background $bgColor
				color :#fff
    }
		.header-left{
				margin-left .1rem
		}
		.header-input{
			flex 1
			height .64rem
			background #ffffff
			line-height .64rem
			border-radius .1rem
			color #cccccc
			margin-right .1rem
			margin-left .1rem
			padding-left .2rem
		}

		.header-right{
			text-align center
			margin-right .1rem
			color #ffffff
		}
		.back-icon{
			text-align center
			font-size 0.4rem
		}
		.arrow-left{
			margin-left  -.14rem
		}
</style>
