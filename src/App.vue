<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <slider v-bind:imgList="img_list"
            v-bind:timeout="timeout"
    ></slider>
  </div>
</template>

<script>
import slider from './components/slider.vue'

import img1 from './img/1.jpg'
import img2 from './img/2.jpg'
import img3 from './img/3.jpg'
import img4 from './img/4.jpg'
import img5 from './img/5.jpg'

export default {
  name: 'App',
  components: {
    slider,
  },
  data: function () {
    return {
      img_list: [
          img1,
          img2,
          img3,
          img4,
          img5,
      ],
      timeout:3000
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
