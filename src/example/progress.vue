<template>
  <div id="example" class="progress">
    <loli-header fixed>
      <router-link :to="{path: '/'}" slot="left">返回</router-link>
      <span slot="title">Progress - 进度条</span>
    </loli-header>

    <div class="demo-block-title"><span>基础进度条</span></div>
    <loli-progress :percent="30"></loli-progress>

    <div class="demo-block-title"><span>可设置颜色进度条</span></div>
    <loli-progress :percent="30" color="#2db7f5"></loli-progress>

    <div class="demo-block-title"><span>可设置宽度进度条</span></div>
    <loli-progress :percent="30" color="#2db7f5" :stroke-width="10"><loli-icon class="icon" :icon="icon"/></loli-progress>

    <div class="demo-block-title"><span>显示数值</span></div>
    <loli-progress :percent="30" color="#2db7f5" hide-info></loli-progress>

    <div class="demo-block-title"><span>手动控制进度条</span></div>
    <loli-progress :percent="percent" color="#2db7f5" hide-info></loli-progress>
    <div style="margin-top:10px">
      <loli-button type="default" tag="button" size="small" @click="add"><loli-icon class="icon" :icon="'plus'"/></loli-button>
      <loli-button type="default" tag="button" size="small" @click="minus"><loli-icon class="icon" :icon="'minus'"/></loli-button>
    </div>

     <loli-row>
      <loli-col :span=10>
         <div class="demo-block-title"><span>circle环形进度条</span></div>
         <div class="circle"><loli-progress circle percenttage=20 circleColor="#2db7f5"></loli-progress></div>
      </loli-col>
      <loli-col :span=10 :offset=2>
        <div class="demo-block-title"><span>圆环控制</span></div>
        <div class="circle"><loli-progress circle :percenttage="percenttage" circleColor="#2db7f5"></loli-progress></div>
        <div style="margin-top:10px;display:flex;justify-content:center">
          <loli-button style="margin:0 6px" type="default" tag="button" size="small" @click="circleAdd"><loli-icon class="icon" :icon="'plus'"/></loli-button>
          <loli-button type="default" tag="button" size="small" @click="circleMinus"><loli-icon class="icon" :icon="'minus'"/></loli-button>
        </div>
      </loli-col>
    </loli-row>
  </div>
</template>
<script>
export default {
  name:'example-progress',
  data(){
    return{
      icon:'check-circle',
      percent:10,
      percenttage:10,
    };
  },
  methods:{
    add:function(){
      if(this.percent>=100) return false;
      this.percent += 10;
    },
    minus:function(){
      if(this.percent<=0) return false;
      this.percent -=10;
    },
    circleAdd:function(){
      if(this.percenttage>=100) return false;
      this.percenttage += 10;
    },
    circleMinus:function(){
      if(this.percenttage<=0) return false;
      this.percenttage -=10;
    }
  }
};
</script>
<style lang="stylus" scoped>
.icon
  font-size 12px
  color #2db7f5
.progress
  padding 0 40px
  &-title
    font-size 16px
    height 50px
    line-height 60px
  .circle
    width 140px
    height 140px
</style>


