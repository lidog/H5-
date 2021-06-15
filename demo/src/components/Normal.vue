<template>
  <h1>@media</h1>
  <h3 class="info">clientWidth: {{clientWidth}} px</h3>
  <h3 class="info">dpr: {{dpr}}</h3>
  <p class="info font16">可以根据屏幕不同改变布局，同时更宽的屏幕可以显示更多的内容 (16)</p>
  <ul class="clearfix ul">
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
  <div class="section clearfix">
    <p class="font14">从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。(14)</p>
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
    document.addEventListener('DOMContentLoaded', this.reset, false)
    window.addEventListener('resize', this.reset, false)
    this.setMeta()
  },
  methods: {
    reset(){
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
.ul li {
  width: 75px;
  height: 75px;
  background: red;
  margin: 5px;
  float: left;
  color: #fff;
  line-height: 75px;
}
.pic {
  img {
    width: 200px;
    height: 180px;
  }
}
.font16 {
  font-size: 16px;
}
.font14 {
  font-size: 14px;
}
.info {
  text-align: left;
  margin-top: 5px;
}
.section {
  margin: 10px 0 20px 0;
  text-align: left;
  text-indent: 2em;
  p {
    width: 75%;
    float: left;
  }
  img {
    width: 25%;
    float: right;
  }
}
@media screen and (max-width: 400px) {
  .section {
    p{
      float: none;
      width: 100%;
    }
    img {
      float: none;
      width: 100%;
    }
  }
}
</style>