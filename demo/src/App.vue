<template>
  <div class="page">
    <!-- <Normal></Normal> -->
    <!-- <Rem></Rem> -->
    <!-- <Flexible></Flexible> -->
    <!-- <FlexiblePro></FlexiblePro> -->
    <!-- <Vw></Vw> -->
    <!-- <FlexibleSDK></FlexibleSDK> -->
    <!-- <Scale></Scale> -->
    <ToVW></ToVW>
 </div>
</template>

<script>
import Normal from "./components/Normal.vue"
import Rem from "./components/Rem.vue"
import Flexible from "./components/Flexible.vue"
import FlexiblePro from "./components/FlexiblePro.vue"
import Scale from "./components/Scale.vue"
import Vw from "./components/Vw.vue"
import FlexibleSDK from "./components/FlexibleSDK.vue"
import ToVW from './components/ToVW.vue'

export default {
  name: 'App',
  components: {
    Normal,
    Rem,
    Flexible,
    FlexiblePro,
    Scale,
    Vw,
    FlexibleSDK,
    ToVW,
  }
}
</script>

<style lang="scss" scoped>
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, dl, dt, dd, ul, ol, li, pre, form, fieldset, legend, button, input, textarea, th, td { margin:0; padding:0;box-sizing: border-box; }
body, button, input, select, textarea { font:12px/1.5tahoma, arial, \5b8b\4f53; font-size: inherit; }
address, cite, dfn, em, var { font-style:normal; }
code, kbd, pre, samp { font-family:couriernew, courier, monospace; }
small{ font-size:14px; }
ul, ol { list-style:none; }
a { text-decoration:none; color:#000;}
a:hover { text-decoration:none; }
sup { vertical-align:text-top; }
sub{ vertical-align:text-bottom; }
legend { color:#000; }
fieldset, img { border:0; }
button, input, select, textarea { font-size:100%; }
table { border-collapse:collapse; border-spacing:0; }
input{-webkit-appearance: none;}
.page {
  padding: 10px;
}
</style>
