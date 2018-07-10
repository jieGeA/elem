<template>
	<div id="cart-control">
		<span class="decrease icon-minus" v-show="food.count > 0" @click="remove"></span>
		<span class="count" v-show="food.count > 0">{{food.count}}</span>
		<span class="increase icon-plus" @click="add" ></span>
	</div>
</template>

<script>
	import Vue from 'vue'
	export default{
		props:{
			food:{
				type:Object,
			}
		},
		methods:{
			add(event){
				if(event._constructed){
					if(!this.food.count){
						Vue.set(this.food,'count')
						this.food.count = 1
					}else{
						this.food.count ++
					}
				}
			},
			remove(event){
				if(this.food.count === 0){
					return 
				}
				this.food.count --
			}
		}
	}
</script>

<style lang="stylus" ref="stylesheet/stylus">
@import '../assets/stylus/index.styl'
#cart-control
 font-size 0
 .icon-plus ,.icon-minus
  display inline-block
  font-size 24px
  width 20px
  height 20px
  line-height 20px
 .decrease , .increase
  padding 6px
  display inline-block
  line-height 20px
  color #00a0dc
  font-size 20px 
 .count
  display inline-block
  text-align center
  width 12px
  font-size 16px
  color rgb(147,153,159) 
  line-height 20px
  padding-top 6px
  vertical-align top
</style>