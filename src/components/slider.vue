<template>
  <div>
    <div v-for="(img, i) in imgList" v-bind:key="i">
      <img v-if="i === active" :src="img" alt="img" @mousemove="stopPlay" @mouseout="atuoPlay">
    </div>

    <sliderIndicator v-bind:imgList="imgList"
                     v-bind:active="active"
                     v-on:indicatorSlideImg="slideImg"
                     v-on:indicatorStop="stopPlay"
                     v-on:indicatorPlay="atuoPlay"
    ></sliderIndicator>
  </div>
</template>

<script>
import SliderIndicator from './sliderIndicator'

export default {
  name: "slider",

  components: {
    SliderIndicator
  },
  props:[
    'imgList',
    'timeout',
  ],
  data: function () {
    return {
      active : 0,
      img_length: this.imgList.length,
      interval_id : '',
      indicator_id: 0,
    }
  },

  methods: {
    atuoPlay: function () {
      if (!this.interval_id) {
        this.interval_id = setInterval(()=>{
          this.active = (this.active + 1) % this.img_length
        }, this.timeout)
      }
    },

    stopPlay: function () {
      if (this.interval_id) {
        clearInterval(this.interval_id)
        console.log('clear')
        this.interval_id = ''
      }
    },

    slideImg: function (i) {
      this.active = i
    }
  },


  created() {
    this.atuoPlay()
  },

}
</script>

<style scoped>

</style>