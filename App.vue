<template>
  <div id="app" v-cloak v-on="{  
      touchstart: ts, //touchstart:触摸事件
      touchmove: tm,  //手指滑动事件
      touchend: te   //手指离开
    }">
    <top></top>
    <index-video v-for='(item,index) in videos' :video='item' :key='index'></index-video>
    <router-view></router-view>
  </div>
</template>
<script>
  import Hello from '~/Hello'
  import test1 from '~/test1'
  import header from '@/commons/header'
   import video from '@/commons/video'
  import rem from '../static/rem'
  export default {
    name: 'app',
    data () {
      return{
        videos:[
          {
            type:1,
            src:'http://r1.ykimg.com/0515000059CC3A21ADC0B0C11003F6C2',
            time:'27:59',
            title:'盘点老炮儿冯小刚的电影生涯',
            playTimes:'3.1万',
            commentTimes:34
          },
          {
            type:1,
            src:'http://r1.ykimg.com/0515000059CC3A21ADC0B0C11003F6C2',
            time:'27:59',
            title:'盘点老炮儿冯小刚的电影生涯',
            playTimes:'3.1万',
            commentTimes:34
          },
          {
            type:2,
            src:'http://r1.ykimg.com/0515000059CC3A5BADC0AEAF100D106E',
            now:'更新至42',
            title:'香港剧<反黑>火爆全球',
            detail:'红枣夫妇背后抱猛撒糖'
          },
          {
            type:2,
            src:'http://r1.ykimg.com/0515000059CC3A5BADC0AEAF100D106E',
            now:'更新至42',
            title:'香港剧<反黑>火爆全球',
            detail:'红枣夫妇背后抱猛撒糖'
          }
        ],
        point:{
          startX:'',
          endX:''
        }
      }
    },
    mounted(){
      rem.adapt(320,100)
    },
    methods:{
      ts(e){
        let finger = e.touches[0]
        this.point.startX=finger.clientX
        this.point.endX='nan'
      },
      tm(e){
        let finger = e.touches[0]
        this.point.endX=finger.clientX
      },
      te(e){
        let distand = this.point.endX-this.point.startX  
        if (distand < -30 ) {
          this.$router.go(-1)
        } else if(distand > 0){
          this.$router.go(1)
        }
      }
    },
    components:{
      test : test1,
      top:header,
      'index-video':video,
      Hello:Hello
    }
  }
</script>
<style>
/*
html{
  font-size:calc( 100vw / 6.4 );   1rem=100px
}*/
*{
  margin:0;
  padding:0;
}
  #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 /* text-align: center;*/
  color: #2c3e50;
 /* margin-top: 60px;*/
  }
</style>
