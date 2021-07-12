<template>
  <p class="info font16">可以根据屏幕不同改变布局，同时更宽的屏幕可以显示更多的内容 (16)</p>
  <div class="border"></div>
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
    <div class="big-img"></div>
  </div>
  <div class="section clearfix">
    <p class="font14">从上世纪60年代袁隆平开始寻找雄性不育的水稻植株用于杂交水稻研究，到今天第三代杂交水稻技术迈向应用转换阶段，有望突破水稻亩产1200斤的天花板。半个世纪以来袁老都将自己投入进稻田，在泥泞当中寻找他想要能解决中国粮食问题的钥匙。(14)</p>
    <div class="small-img"></div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@mixin background-url-dpr($url) {
  background-image: url("http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/" + $url + ",jpg");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  @media screen and (-webkit-min-device-pixel-ratio: 1) and (-webkit-min-device-pixel-ratio: 1.5) {
    background-image: url("http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_25/" + $url + ",jpg");
  }
  @media screen and (-webkit-min-device-pixel-ratio: 1.5) and (-webkit-min-device-pixel-ratio: 2) {
    background-image: url("http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_75/" + $url + ",jpg");
  }
  @media screen and (-webkit-min-device-pixel-ratio: 2) and (-webkit-min-device-pixel-ratio: 3) {
    background-image: url("http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_100/" + $url + ",jpg");
  }
  @media screen and (-webkit-min-device-pixel-ratio: 3) and (-webkit-min-device-pixel-ratio: 4) {
    background-image: url("http://image-demo.oss-cn-hangzhou.aliyuncs.com//smile.jpg?x-oss-process=image/resize,w_200,h_200/auto-orient,1/quality,q_100/" + $url + ",jpg");
  }
}
@mixin font-size-dpr($fontSize) {
  font-size: $fontSize;
  @media screen and (-webkit-min-device-pixel-ratio: 1) and (-webkit-min-device-pixel-ratio: 1.5) {
    font-size: $fontSize;
  }
  @media screen and (-webkit-min-device-pixel-ratio: 1.5) and (-webkit-min-device-pixel-ratio: 2) {
    font-size: $fontSize * 2;
    zoom: 0.5;
  }
  //for mx3
  @media screen and (-webkit-min-device-pixel-ratio: 2) and (-webkit-min-device-pixel-ratio: 2.5) {
    font-size: $fontSize * 2;
    zoom: 0.5;
  }
  //for 小米note,for 小米mix
  @media screen and (-webkit-min-device-pixel-ratio: 2.5) and (-webkit-min-device-pixel-ratio: 2.75) {
    font-size: $fontSize * 2.2;
    zoom: 0.4545;
  }
  @media screen and (-webkit-min-device-pixel-ratio: 2.75) and (-webkit-min-device-pixel-ratio: 3) {
    font-size: $fontSize * 2.2;
    zoom: 0.4545;
  }
  //for 三星note4 ,三星s6
  @media screen and (-webkit-min-device-pixel-ratio: 3) and (-webkit-min-device-pixel-ratio: 4) {
    font-size: $fontSize * 2;
    zoom: 0.5;
  }
}
@mixin border-dpr() {
  @media screen and (-webkit-min-device-pixel-ratio: 1) and (-webkit-min-device-pixel-ratio: 1.5) {
    height: 1px;
  }
  @media screen and (-webkit-min-device-pixel-ratio: 1.5) and (-webkit-min-device-pixel-ratio: 2) {
    height: 2px;
    transform: scaleY(0.5);
  }
  @media screen and (-webkit-min-device-pixel-ratio: 2) and (-webkit-min-device-pixel-ratio: 3) {
    height: 3px;
    transform: scaleY(0.333);
  }
  @media screen and (-webkit-min-device-pixel-ratio: 3) and (-webkit-min-device-pixel-ratio: 4) {
    height: 4px;
    transform: scaleY(0.25);
  }
}
.clearfix {
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
.border {
  width: 100%;
  @include border-dpr();
  background: #000;
  margin: 1.333vw 0;
}
.ul li {
  width: 20vw;
  height: 20vw;
  background: red;
  margin:1.333vw;
  float: left;
  color: #fff;
  line-height:20vw;
}
.pic {
  .big-img {
    width: 53.333vw;
    height: 48vw;
    @include background-url-dpr("format");
  }
}
.font16 {
  @include font-size-dpr(16px);
}
.font14 {
  @include font-size-dpr(14px);
}
.info {
  text-align: left;
  margin-top: 1.333vw;
}
.section {
  margin: 2.667vw 0 5.333vw 0;
  text-align: left;
  text-indent: 2em;
  p {
    width: 75%;
    float: left;
  }
  .small-img {
    width: 25%;
    height: 150px;
    float: right;
    @include background-url-dpr("format");
  }
}
</style>