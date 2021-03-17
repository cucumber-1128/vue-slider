<template>
  <div class="slider-indicators">
    <div v-for="(img, i) in imgList" v-bind:key="i">
      <div v-if="active === i"
           class="slider-indicator red"
           @mousemove="stopPlay"
           @mouseout="autoPlay"
      >
      </div>
      <div v-else class="slider-indicator"
           @mousemove="indicatorSlideImg(i); stopPlay"
           @mouseout="autoPlay"
      >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SliderIndicator",
  props: [
      'imgList',
      'active'
  ],
  data: function () {
    return {

    }
  },
  methods: {
    indicatorSlideImg: function (i) {
      this.$emit('indicatorSlideImg', i)
    },
    stopPlay: function () {
      this.$emit('indicatorStop')
    },
    autoPlay: function () {
      this.$emit('indicatorPlay')
    }
  },
}
</script>

<style scoped>
  .slider-indicators {
    display: flex;
    justify-content: center;
  }

  .slider-indicator {
    width: 10px;
    height: 10px;
    background: #9c8c8c;
    margin: 5px;
    border-radius: 50%;
  }
  .red {
    background: red!important;
  }

</style>