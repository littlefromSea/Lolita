<template>
<div>
   <div v-if="circle" class="loli-progress-circle">
     <svg viewBox="0 0 100 100">
       <path d="M 50 50 m 0 -47 a 47 47 0 1 1 0 94 a 47 47 0 1 1 0 -94" stroke="#e5e9f2" stroke-width="4.8" fill="none" class="el-progress-circle__track"></path>
       <path d="M 50 50 m 0 -47 a 47 47 0 1 1 0 94 a 47 47 0 1 1 0 -94" 
          :stroke-dashoffset="percenttageInfo" 
          :stroke="circleColor"
          stroke-linecap="round"  
          stroke-width="4.8" 
          fill="none"
          style="stroke-dasharray: 299.08px, 299.08px; transition: stroke-dashoffset 0.6s ease 0s, stroke 0.6s ease;">
       </path>
     </svg>
     <div>{{percenttage}}%</div>
  </div>
  <div class="loli-progress-bar" v-else>
    <div class="loli-progress-slver" :style="{height:strokeWidth+'px'}">
      <div class="loli-progress-slver-contral" :style="{width:percent+'%',backgroundColor:color}">
      </div>
    </div>
    <div class="loli-pregress-percent" v-if="hideInfo">{{percent}}%</div>
    <div class="loli-pregress-percent"><slot></slot></div>
  </div>
</div>
</template>
<script>
export default {
  name:'loli-progress',
  computed:{
    percenttageInfo:function(){
      var percent = this.percenttage / 100;
      return (300 - 300 * percent) + 'px';
    }
  },
  props:{
    percent:Number,
    color:{
      type:String,
      default:'#f69433'
    },
    strokeWidth:{
      type:Number,
      default: 3
    },
    hideInfo:{
      type:Boolean,
      default:false
    },
    circle:{
      type:Boolean,
      default:false
    },
    circleColor:{
      type:String,
      default:'#20a0ff'
    },
    percenttage:[Number,String]
  },
};
</script>

<style lang="stylus" scoped> 
.loli-progress-circle
  position relative
  div
    position absolute 
    left 50%
    top 50%
    transform translate(-50%,-50%)
.loli-progress-bar
  display flex
  align-items center
  .loli-progress-slver
    position relative 
    background #ebebeb
    overflow hidden
    border-radius 4px
    flex 1
    &-contral
      position absolute 
      left 0
      top 0 
      height 100%
      transition .3s all ease
      border-radius 4px
  .loli-pregress-percent
    margin 0 6px
  .circle
    -webkit-transition stroke-dasharray .25s
    transition stroke-dasharray .25s
</style>


