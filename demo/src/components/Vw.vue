<template>
  <h1>Vw</h1>
  <h3 class="info">clientWidth: {{clientWidth}} px</h3>
  <h3 class="info">dpr: {{dpr}}</h3>
  <h3 class="info font16">vw 转换为rem，只需要rem*10</h3>
  <div class="border border-bt-1px"></div>
  <ul class="ul clearfix">
    <li>75*75</li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
  </ul>
  <div class="pic flex">
    <div class="big-img bg"></div>
  </div>
  <div class="section flex">
    <p>从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。</p>
    <div class="small-img bg"></div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      dpr: 1,
      clientWidth: 0,
    }
  },
  mounted(){
    document.addEventListener('DOMContentLoaded', this.reset, false)
    window.addEventListener('resize', this.reset, false)
    this.setMeta()
  },
  methods: {
    reset(){
      this.clientWidth = document.documentElement.clientWidth
      this.dpr = window.devicePixelRatio
      document.documentElement.setAttribute('data-dpr', this.dpr)
    },
    setMeta(){
      let metaEl = document.createElement('meta');
      metaEl.setAttribute('name', 'viewport');
      metaEl.setAttribute('content', 'width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover');
      document.querySelector('head').appendChild(metaEl)
    },
  }
}
</script>
<style lang="scss" scoped>
@mixin background-url-dpr($url) {
    background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/'+ $url +',jpg');
    background-repeat: no-repeat;
    background-size: 100% 100%;
  [data-dpr="1"] & { 
    background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/'+ $url +',jpg');
  } 
  [data-dpr="2"] & {
    background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_75/'+ $url +',jpg');   
  } 
  [data-dpr="3"] & {
    background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_100/'+ $url +',jpg');
  } 
  [data-dpr="4"] & {
    background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_100/'+ $url +',jpg');
  } 
}
.border-bt-1px{
    position: relative;
    &:before{
      content: '';
      position: absolute;
      left:0;           
      bottom: 0;
      width: 100%;
      height: 1px;
      background: #ee2c2c;
      transform: scaleY(0.5);
    }
  }
.clearfix{
  zoom: 1;
  &::after {
    content: "";
    display: block;
    height: 0;
    clear: both;
  }
}
.flex {
  display: flex;
  justify-content: center;
}
.border{
  width: 100%;
  height: 1px;
  // background: #000;
  margin: 10px 0;
}
.ul li {
  width: 20vw /* 150/75 */;
  height: 20vw /* 150/75 */;
  background: red;
  margin: .133333rem /* 10/75 */;
  float: left;
  color: #fff;
  line-height: 20vw;
}
.bg{
  background-image: url('http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/format,jpg');
  background-repeat: no-repeat;
  background-size: 100% 100%;
}
.big-img {
  width: 53.33333vw /* 400/75 */;
  height: 48vw /* 360/75 */;
  @include background-url-dpr('format')
}
.font16{
  font-size: 16px;
}
.section {
  margin: 2.6666667vw 0 5.3333333vw 0;
  text-align: left;
  text-indent: 2em;
   p {
    width: 75vw /* 562.5/75 */;
  }
  .small-img {
    width: 25vw;
    height: 25vw;
    @include background-url-dpr('format')
  }
}
.info {
  text-align: left;
  margin-top: 1.3333333vw;
}
</style>