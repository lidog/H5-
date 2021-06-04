<template>
  <h1>各种缩放的对比</h1>
  <h3 class="info">clientWidth: {{clientWidth}} px</h3>
  <h3 class="info">dpr: {{dpr}}</h3>
  <p class="info font16">{{tips}}</p>
  <div class="border"></div>
  <div class="mt3 flex">
    控制html 的fontsize，就可以控制元素大小
    <button @click="min">缩小-</button>
    <button @click="max">放大+</button>
  </div>
  <div class="mt3 flex">
    控制initial-scale 适配
    <button @click="cut">缩小-</button>
    <button @click="add">放大+</button>
  </div>
  <div class="mt3 flex">
    控制transfrom 适配
    <button @click="less">缩小-</button>
    <button @click="more">放大+</button>
  </div>
  <div class="mt3 flex">
    控制zoom 适配
    <button @click="lessZoom">缩小-</button>
    <button @click="moreZoom">放大+</button>
  </div>
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
    <p>从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。</p>
    <img src="http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/format,jpg">
  </div>
</template>

<script>
export default {
  data(){
    return {
      dpr: 1,
      clientWidth: 0,
      scale: 1,
      transFromScale: 1,
      zoom: 1,
      tips: "rem缩放与scale缩放的对比",
      scaleTips: "1: 视口在变化。2：元素大小没有变化。",
      remTips: "1: 视口没有变化；2: 元素大小在改变。",
      transformTips: "像手机缩放图片一样缩放页面，会产生横向滚动条，不适用于适配",
      zoomTips: "也是缩放视口，兼容性存在问题",
    }
  },
  mounted(){
    document.addEventListener('DOMContentLoaded', this.reset, false)
    this.setMeta()
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
    min(){
      let html = document.documentElement
      html.style.fontSize = parseFloat(html.style.fontSize, 3) - 5 + 'px'
      this.tips = this.remTips
    },
    max(){
      let html = document.documentElement
      html.style.fontSize =  parseFloat(html.style.fontSize, 3)  + 5 + 'px'
      this.tips = this.remTips
    },
    cut(){
      this.scale = (this.scale*10 - 1) / 10
      let mate = document.createElement('meta')
      mate.setAttribute('name', 'viewport')
      mate.setAttribute('content', 'initial-scale='+ this.scale)
      document.querySelector('head').appendChild(mate)
      this.getWidth()
      this.tips = this.scaleTips
    },
    add(){
      this.scale = (this.scale*10 + 1) / 10
      let mate = document.createElement('meta')
      mate.setAttribute('name', 'viewport')
      mate.setAttribute('content', 'initial-scale='+ this.scale)
      document.querySelector('head').appendChild(mate)
      this.getWidth()
      this.tips = this.scaleTips
    },
    less(){
      this.transFromScale = (this.transFromScale*10 - 1) / 10
      let html = document.documentElement
      html.style.transformOrigin = `0% 0%`
      html.style.transform = `scale(${this.transFromScale})`
      this.tips = this.transformTips
    },
    more(){
      this.transFromScale = (this.transFromScale*10 + 1) / 10
      let html = document.documentElement
      html.style.transformOrigin = `0% 0%`
      html.style.transform = `scale(${this.transFromScale})`
      this.tips = this.transformTips
    },
    lessZoom(){
      this.zoom = (this.zoom*10 - 1) / 10
      let html = document.documentElement
      html.style.zoom = `${this.zoom}`
    },
    moreZoom(){
      this.zoom = (this.zoom*10 + 1) / 10
      let html = document.documentElement
      html.style.zoom = `${this.zoom}`
    }
  }
}
</script>

<style>
body {
  font-size: 14px;
}
</style>
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
.mt3{
  margin-top: .08rem;
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
  width: 1.5rem;
  height: 1.5rem;
  background: red;
  margin: 0.1rem;
  float: left;
  color: #fff;
  line-height: 2rem;
}
.pic {
  img {
    width: 4rem;
  }
}
.font16 {
  font-size: 16px;
}
.section {
  margin: 0.2rem 0 0.4rem 0; 
  text-align: left;
  text-indent: 2em;
  p {
    width: 5.623rem;
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