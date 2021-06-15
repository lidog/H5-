<template>
  <h1>rem</h1>
  <h3 class="info">clientWidth: {{clientWidth}} px</h3>
  <h3 class="info">dpr: {{dpr}}</h3>
  <p class="info font16 font16-rem">屏幕变化，元素自动伸缩,以适配不同屏幕（16）</p>
  <div class="border"></div>
  <ul class="ul clearfix">
    <li>75*75</li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
  </ul>
  <div class="pic">
    <img src="http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/format,jpg">
  </div>
  <div class="section flex">
    <p class="font14 font14-rem">从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。（14）</p>
    <img src="http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/format,jpg">
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
    this.setMeta()
    document.addEventListener('DOMContentLoaded', this.reset, false)
    window.addEventListener('resize', this.reset, false)
  },
  methods: {
    reset(){
      this.getWidth()
      let html = document.documentElement
      html.style.fontSize = (html.clientWidth / 750) * 100 + 'px'
    },
    getWidth(){
      this.clientWidth = document.documentElement.clientWidth
      this.dpr = window.devicePixelRatio
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
}
.border{
  width: 100%;
  height: 1px;
  background: #000;
  margin: 0.2rem 0;
}
.ul li {
  width: 1.5rem; /* 设计稿上是150，150/100 */;
  height: 1.5rem;
  background: red;
  margin: 0.1rem;
  float: left;
  color: #fff;
  line-height: 75px;
}
.pic {
  img {
    width: 4rem;
  }
}
.font16 {
  font-size: 16px;
}
.font16-rem {
  font-size: 0.16rem
}
.font14 {
  font-size: 14px;
}
.font14-rem {
  font-size: 0.14rem
}
.section {
  margin: 0.2rem 0 0.4rem 0; 
  p {
    text-align: left;
    text-indent: 2em;
    width: 5.625rem;
  }
  img {
    width: 1.875rem;
    height: auto;
  }
}
.info {
  text-align: left;
  margin-top: 0.1rem;
}
</style>