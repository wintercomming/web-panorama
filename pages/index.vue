
  <template>
   <div class="title" style="width:100%;height:100%;">
     <div id="pano" style="width:100%;height:100%;"><noscript><table style="width:100%;height:100%;">
       <tr style="vertical-align:middle;text-align:center;">
         <td>ERROR:<br><br>Javascript not activated<br><br></td></tr>
     </table>
     </noscript>
       <transition name = "layer_fade">
         <div class="layer" v-if="showlayer">
           <div class="layer_info">
             <p class="layer_title">四季农场</p>
             <p class="layer_child">坐标:66.666N 88.888E</p>
             <p class="layer_child">2018-09-09 15:09:00</p>
             <p class="layer_child">————————</p>
             <p class="layer_child">空气温度:28.6℃</p>
             <p class="layer_child">空气湿度:88%</p>
             <p class="layer_child">露点温度:28.6℃</p>
             <p class="layer_child">光照强度:35.0lux</p>
             <p class="layer_child">降雨量:0mm</p>
             <p class="layer_child">风力:10m/s</p>
             <p class="layer_child">气压:900.5hpa</p>
           </div>
         </div>
       </transition>
       <div class="mouse" v-if="showpicture">
         <img src="mouse.png" class="farm_mouse_picture">
       <p class="mouse_title">左键拖动鼠标查看</p>
       </div>
       <transition name="fade"><div class="farm_information" v-if="show">
         <div class="farm_close_icon" @click="show =!show">
           <img src="icon/icon09.png"></div><div class="farm_picture">
       </div>
  <div class="farm_text">
  <p class="farm_text_title">大气农场</p>
  <p class="farm_hostname">农场主</p>
  <button class="farm_button">去店铺逛逛</button>
  </div>
  </div>
  </transition>
  </div>
  <div class="icon" >
  <div class="icon1 icon_child" v-on:mouseover="changeicon1color()" v-on:mouseleave="backicon1color" id="icon1"></div>
    <a href="/"> <div class="icon2 icon_child" v-on:mouseover="changeicon2color()" v-on:mouseleave="backicon2color" id="icon2"></div></a>
  <div class="icon3 icon_child" v-on:mouseover="changeicon3color()" v-on:mouseleave="backicon3color" id="icon3" v-on:click="showlayer =!showlayer"></div>
  <div class="icon4 icon_child" v-on:mouseover="changeicon4color()" v-on:mouseleave="backicon4color" id="icon4" v-on:click="show =!show"></div>
  </div>
  </div>
  </template>

  <script>


  export default {
    components: {},
  head() {
    return {
    script: [{src: '/krpano.js'}]
  }
  },
  mounted() {
  //console.log(embedpano)
    setInterval(this.closepicture,2000)
  embedpano({
    swf: "krpano.swf",
    xml: "krpano.xml",
    target: "pano",
    html5: "auto",
    mobilescale: 1.0,
    passQueryParameters: true
  });
  },
  data(){
  return{
    show:false,
    showlayer:true,
    showpicture:true
  }
  },
  methods: {
      closepicture:function(){
        this.showpicture=false;
      },
  changeicon1color: function () {
    document.getElementById("icon1").style.backgroundImage = "URL(icon/icon04.png)";
  },
  backicon1color: function () {
    document.getElementById("icon1").style.backgroundImage = "URL(icon/icon08.png)";
  },
  changeicon2color: function () {
    document.getElementById("icon2").style.backgroundImage = "URL(icon/icon05.png)";
  },
  backicon2color: function () {
    document.getElementById("icon2").style.backgroundImage = "URL(icon/icon01.png)";
  },
  changeicon3color: function () {
    document.getElementById("icon3").style.backgroundImage = "URL(icon/icon06.png)";
  },
  backicon3color: function () {
    document.getElementById("icon3").style.backgroundImage = "URL(icon/icon02.png)";
  },
  changeicon4color: function () {
    document.getElementById("icon4").style.backgroundImage = "URL(icon/icon07.png)";
  },
  backicon4color: function () {
    document.getElementById("icon4").style.backgroundImage = "URL(icon/icon03.png)";
  },
  },
  }
  </script>

  <style>
      html,body{
        margin:0;
        height:100%;
      }
  .title{
    position: absolute;
  }
  .layer{
    position:absolute;
    bottom:0;
    left:1%;
    width:270px;
    height: 50%;
    background-color:rgba(0,0,0,0.4);
    z-index:2;
    color:rgba(255,255,255,0.95);
    font-family: "Yu Gothic UI";
    font-weight: bold;
    border-top-left-radius: 10px ;
    border-top-right-radius: 10px ;
  }
  .icon{
    position: absolute;
    z-index:2;
    right:1%;
    top:3%;
  }
  .icon1{background: url("../static/icon/icon08.png")}
  .icon2{background: url("../static/icon/icon01.png")}
  .icon3{background: url("../static/icon/icon02.png")}
  .icon4{background: url("../static/icon/icon03.png")}
  .icon_child{
    margin-top:15%;
    height:40px;
    width: 40px;
  }
  .layer_info{
    margin-left:10%;
  }
  .layer_title{
    font-size: 24px;
    margin-top:7%;
  }
  .layer_child{
    font-size:16px;
    margin-top:8%;
  }
  .farm_information{
    border:1px rgba(0,0,0,0.8) solid;
    width:300px;
    height:350px;
    position:absolute;
    z-index: 2;
    top:50%;
    left:50%;
    margin-left:-150px;
    margin-top:-175px;
    background: rgba(0,0,0,0.75);
    color:rgba(255,255,255,0.9);
    font-family: 楷体;
    font-weight: bold;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
  }
  .farm_close_icon{
    position:absolute;
    right:-15px;
    top:-16px;
  }
  .farm_picture{
    background: url("../static/picture1.jpg");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    width:100%;
    height:60%;
  }
  .farm_text_title{
    height:40%;
    text-align: center;
    font-size:20px;
    margin-top: 8%;
  }
  .farm_hostname{
    text-align: center;
    font-size: 14px;
    margin-top:5%;
    color:rgba(255,255,255,0.6);
  }
  .farm_button{
    display: block;
    margin-left: auto;
    margin-right:auto;
    margin-top:6%;
    background:rgba(0,0,0,0.65);
    width:50%;
    height:30px;
    border-color: aquamarine;
    border-radius: 25px;
    font-size: 16px;
    font-family: 楷体;
    color:rgba(255,255,255,0.9);
  }
  .mouse{
    position: absolute;
    width: 150px;
    height: 150px;
    top:50%;
    left:50%;
    margin-top:-75px;
    margin-left:-75px;
    z-index: 2;
  }
  .mouse_title{
    color:rgba(255,255,255,0.9);
    font-size:13px;
   position: absolute;
    bottom:20px;
    left:25px;
  }
  .farm_mouse_picture{
    width:150px;
    height:150px;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  .layer_fade-enter-active {
    transition: all .2s ease;
  }
  .layer_fade-leave-active {
    transition: all .2s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .layer_fade-enter, .layer_fade-leave-to {
    transform: translateX(10px);
    opacity: 0;
  }

</style>
