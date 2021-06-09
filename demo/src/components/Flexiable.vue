<template>
  <h1>flexiable</h1>
  <h3 class="info">clientWidth: {{clientWidth}} px</h3>
  <h3 class="info">dpr: {{dpr}}</h3>
  <p class="info">屏幕变化，缩放整体,以适配不同屏幕(16)</p>
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
    <p>从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。(14)</p>
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
    this.setFlexiable()
    document.addEventListener('DOMContentLoaded', this.reset, false)
    window.addEventListener('resize', this.reset, false)
  },
  methods: {
    reset(){
      this.clientWidth = document.documentElement.clientWidth
      this.dpr = window.devicePixelRatio
    },
    setFlexiable(){
      let scritp = document.createElement('script')
      scritp.setAttribute('src', '/src/flexible.js')
      document.documentElement.appendChild(scritp)
    }
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
  margin: .26666667rem 0;
}
.ul li {
  width: 2rem /* 150/75 */;
  height: 2rem /* 150/75 */;
  background: red;
  margin: .133333rem /* 10/75 */;
  float: left;
  color: #fff;
  line-height: 2rem;
}
.pic {
  img {
    width: 5.333333rem /* 400/75 */;
    height: 4.8rem /* 360/75 */;
  }
}
.section {
  margin: .26666667rem 0 .53333333rem 0;
  text-align: left;
  text-indent: 2em;
   p {
    width: 7.5rem /* 562.5/75 */;
  }
  img {
    width: 2.5rem;
  }
}
.info {
  text-align: left;
  margin-top: .13333333rem;
}
</style>