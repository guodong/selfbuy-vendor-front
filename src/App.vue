<template>
  <div id="app">
    <div class="cates">
      <a v-on:click="linshi">休闲零食</a>
      <a v-on:click="yinliao">果汁饮料</a>
      <a v-on:click="kuaican">方便快餐</a>
    </div>
    <div class="container">
      <div class="room room--current" id="room">
        <div class="room__side room__side--back">
          <div class="shelf">
            <div class="brand">
              <div class="brand-inner" v-on:click="goin">
                果汁饮料
              </div>
            </div>
            <div class="row" v-for="(r, index) in rows + 1" v-bind:style="{ top: (r-1)/rows * 100 + '%' }">
            </div>
            <div class="column" v-for="(c, index) in columns + 1" v-bind:style="{ left: (c-1)/columns * 100 + '%' }"></div>
            <ul>
              <li v-for="n in 21">
                <img src="/static/coco.png">
                <div class="tag">
                  <span class="inner">
                    可口可乐 ¥2.50
                  </span>
                </div>
              </li>
            </ul>
          </div>
        </div>
        <div class="room__side room__side--left" id="room__side--left">
          <div class="shelf">
            <div class="brand">
              <div class="brand-inner">
                休闲食品
              </div>
            </div>

            <div class="row" v-for="(r, index) in rows + 1" v-bind:style="{ top: (r-1)/rows * 100 + '%' }">
            </div>
            <div class="column" v-for="(c, index) in columns + 1" v-bind:style="{ left: (c-1)/columns * 100 + '%' }"></div>
            <ul>
              <li v-for="n in 21">
                <img src="/static/coco.png">
                <div class="tag">
                  <span class="inner">
                    可口可乐 ¥2.50
                  </span>
                </div>
              </li>
            </ul>
          </div>
        </div>
        <div class="room__side room__side--right">
          <div class="shelf">
            <div class="brand">
              <div class="brand-inner">
                方便快餐
              </div>
            </div>

            <div class="row" v-for="(r, index) in rows + 1" v-bind:style="{ top: (r-1)/rows * 100 + '%' }">
            </div>
            <div class="column" v-for="(c, index) in columns + 1" v-bind:style="{ left: (c-1)/columns * 100 + '%' }"></div>
            <ul>
              <li v-for="n in 21">
                <img src="/static/coco.png">
                <div class="tag">
                  <span class="inner">
                    可口可乐 ¥2.50
                  </span>
                </div>
              </li>
            </ul>
          </div>
        </div>
        <div class="room__side room__side--bottom"></div>
      </div><!-- /room -->


    </div>

    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      rows: 3,
      columns: 7
    }
  },
  methods: {
    yinliao() {
      //document.getElementById('room').style.transform = 'rotate3d(0, 1, 0, 90deg) translateZ( 100px )'
//      document.getElementById('room').style.transform = 'rotate3d(0, 1, 0, 90deg) translateX( 500px ) translateZ( 1500px )'
//      document.getElementById('room__side--left').style.display = 'none'
//      document.getElementById('room').style.display = 'none'
      document.getElementsByClassName('room__side--left')[0].style.opacity = '1'
      document.getElementsByClassName('room__side--right')[0].style.opacity = '1'
      document.getElementById('room').style.transform = 'rotate3d(0, 0, 0, 0deg) translateX( 00px ) translateZ( 2000px )'
    },
    kuaican() {
      document.getElementsByClassName('room__side--left')[0].style.opacity = '0'
      document.getElementsByClassName('room__side--right')[0].style.opacity = '1'
      document.getElementById('room').style.transform = 'rotate3d(0, 1, 0, 90deg) translateX( 1000px ) translateZ( 1500px )'
    },
    linshi() {
      document.getElementsByClassName('room__side--left')[0].style.opacity = '1'
      document.getElementsByClassName('room__side--right')[0].style.opacity = '0'
      document.getElementById('room').style.transform = 'rotate3d(0, 1, 0, -90deg) translateX( -1000px ) translateZ( 1500px )'
    }
  }
}
</script>

<style>
  body,html {
    height: 100%;
    margin: 0;
  }
  body {
    /*background: url("/static/wall.jpg") no-repeat;*/
    background-size: cover;
    background-color: #222;
  }
  .cates {
    text-align: center;
    position: absolute;
    width: 100%;
    z-index: 100;
  }
  .cates a {
    display: inline-block;
    color: #fff;
    width: 240px;
    height: 60px;
    font-size: 28px;
    line-height: 60px;
    background: url("/static/pai.png") no-repeat;
    background-size: cover;
    cursor: pointer;
  }
  .container {
    position: relative;
    overflow: hidden;
    width: 100vw;
    height: 100vh;
    perspective: 2000px;
  }
  .room {
    position: absolute;
    /*top: 50%;*/
    /*left: 50%;*/
    width: 100vw;
    height: 100vh;
    /*margin: -50vh 0 0 -50vw;*/
    pointer-events: none;
    opacity: 0;
    transform-style: preserve-3d;
    transform-origin: 50% 50%;
    transition-duration: 2s;
  }
  .room--current {
    pointer-events: auto;
    opacity: 1;
  }

  .room__side {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    transform-style: preserve-3d;
  }

  .room__side--left,
  .room__side--right {
    width: 3000px; /* depth */
    height: 100vh;
    background: url("/static/wall.jpg");
  }

  .room__side--back {
    width: 100vw;
    height: 100vh;
    background: url("/static/wall.jpg");
    background-size: cover;
    transform: translate3d(0, 0, -3000px);
    /* Rotation due to rendering bug in Chrome when loader slides up (images seem cut off) */
  }

  .room__side--right {
    right: 0;
    /*justify-content: flex-end;*/
    transform: rotate3d(0, 1, 0, -90deg);
    transform-origin: 100% 50%;
  }

  .room__side--left {
    /*justify-content: flex-start;*/
    transform: rotate3d(0, 1, 0, 90deg);
    transform-origin: 0 50%;
  }

  .room__side--bottom {
    width: 100vw; /* depth */
    height: 3000px;
    background: url("/static/ban.jpeg");
    transform: rotate3d(1, 0, 0, 90deg) translate3d(0, -3000px, 0);
    transform-origin: 50% 0%;
  }

  .room__side--bottom {
    top: 100%;
  }

  .shelf {
    width: 80%;
    height: 80%;
    margin: -0px auto;
    transform-style: preserve-3d;
    /*perspective: 1400px;*/
    transition: transform 5s;
    position: absolute;
    transform: translateZ(10px);
    bottom: 2%;
    z-index: 1;
  }

  .brand {
    position: absolute;
    top: -100px;
    width: 100%;
  }
  .brand-inner {
    font-size: 32px;
    margin: 0 auto;
    width: 240px;
    height: 60px;
    line-height: 60px;
    background: url("/static/pai.png") no-repeat;
    background-size: cover;
    font-weight: bold;
    color: #fff;
    text-align: center;
  }
  .row, .column {
    background: url("/static/muban.jpeg");
    background-size: cover;
    position: absolute;
  }
  .row {
    background: url("/static/kong.jpeg");
    /*background-size: cover;*/
    width: 100%;
    height: 100px;
    border: 0px solid black;
    transform: rotateX(   90deg ) translateZ( -0px );
    transform-origin: 0% 0%;
  }
  .column {
    height: 100%;
    width: 100px;
    transform: rotateY(   -90deg ) translateZ( -0px ) translateY(0px);
    transform-origin: 0% 50%;
  }
  .back {
    width: 100%;
    height: 100%;
    background: url("/static/bg.jpeg");
    background-size: cover;
    position: absolute;
    transform: translateY(200px) translateZ(-100px);
  }
  .face {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    transform: translateY(200px) translateZ(50px);
  }
  .face1 {
    transform: translateY(200px) translateZ(90px);
  }
  ul {
    padding: 0;
    margin: 0;
    height: 100%;
    transform: translateZ(90px);
    /*margin-top: 210px;*/
    /*margin-left: -50px;*/
    /*position: absolute;*/
  }
  .shelf li {
    display: block;
    width: 14.285%;
    height: 33.3%;
    float: left;
    position: relative;
  }
  img {
    width: 160px;
    height: 160px;
    margin-left: 20px;
    position: absolute;
    bottom: -5px;
    left: 0;
  }
  .tag {
    margin: 0 auto;
    position: absolute;
    bottom: 0;
    width: 100%;
  }
  .inner {
    background: rgba(255,255,255, .75);
    margin: 0 auto;
    padding: 2px 20px;
    font-size: 12px;

  }
</style>
