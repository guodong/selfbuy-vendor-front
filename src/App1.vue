<template>
  <div id="app">
    <div class="sidebar">
      <ul>
        <li><a v-on:click="go">果汁饮料</a></li>
        <li><a>休闲零食</a></li>
        <li><a>方便快餐</a></li>
        <li><a>生活用品</a></li>
      </ul>
    </div>
    <div class="shelf" id="shelf">
      <div class="brand">
        <div class="brand-inner">
          果汁饮料
        </div>
      </div>
      <div class="back"></div>
      <div class="row" v-for="(r, index) in rows + 1" v-bind:style="{ top: index * 200 + 'px' }">
      </div>
      <div class="column" v-for="(c, index) in columns + 1" v-bind:style="{ left: index * 200 + 'px' }"></div>
      <div class="face">
        <ul>
          <li v-for="(f, index) in rows * columns">
            <img src="/static/coco.png">
          </li>
        </ul>
      </div>
      <div class="face face1">
        <ul>
          <li v-for="(f, index) in rows * columns">
            <div class="tag">
              <span class="inner">
                可口可乐 ¥2.50
              </span>
            </div>
          </li>
        </ul>
      </div>

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
      columns: 5
    }
  },
  methods: {
    go() {
      document.getElementById('shelf').style.perspective = '2000px'
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
    background-color: #343434;
  }
  .sidebar {
    position: absolute;
    left: 0;
    height: 100%;
    padding-top: 180px;
  }
  .sidebar li {
    margin-bottom: 20px;
  }
  .sidebar li a {
    display: block;
    height: 40px;
    width: 160px;
    line-height:40px;
    color: #fff;
    background: url("/static/pai.png") no-repeat;
    background-size: cover;
  }
  .brand {
    position: absolute;
    top: 100px;
    width: 100%;
  }
  .brand-inner {
    font-size: 24px;
    margin: 0 auto;
    width: 240px;
    height: 60px;
    line-height: 60px;
    background: url("/static/pai.png") no-repeat;
    background-size: cover;
    font-weight: bold;
    color: #fff;
  }
  .shelf {
    width: 1000px;
    height: 600px;
    margin: -0px auto;
    transform-style: preserve-3d;
    perspective: 1400px;
    transition: transform 5s;
    position: relative;
  }
  .row, .column {
    background: url("/static/muban.jpeg");
    position: absolute;
  }
  .row {
    background: url("/static/muban1.jpeg");
    width: 100%;
    height: 196px;
    border: 0px solid black;
    transform: rotateX(   90deg ) translateZ( -102px );
  }
  .column {
    height: 100%;
    width: 200px;
    transform: rotateY(   90deg ) translateZ( -100px ) translateY(200px);
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
    /*margin-top: 210px;*/
    /*margin-left: -50px;*/
    /*position: absolute;*/
  }
  .shelf li {
    display: block;
    width: 200px;
    height: 200px;
    float: left;
    position: relative;
  }
  img {
    width: 160px;
    height: 160px;
    margin-left: 20px;
    position: absolute;
    bottom: 0;
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}


</style>
