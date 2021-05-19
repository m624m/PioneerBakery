<template>
  <div class="carousel"
    @mouseover="stop"
    @mouseout="autoPlay"
  >
    <div class="images" 
      v-for="image in images" 
      :key="image.id" 
      :style="{left: toLeft + '%'}" 
      :class="{transition: transition}"
    >
      <img class="img1" :src="image">
      <img class="img2" :src="image">
      <img class="img3" :src="image">
    </div>
    <div class="circle-wrap">
      <div class="circle" 
        v-for="circle in circles"
        :key="circle.id"
        :class="{'circle-fill': circle.fill}"
        @click="select(circle.id)"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  data(){
    return {
      images: images,
      circles: circles,
      toLeft: 0,
      timer: null,
      transition: true,
      index: 0,
    }
  },
  methods: {
    change(offset) {
      let newLeft = this.toLeft + offset;
      if(newLeft >= -300) {
        this.toLeft = this.toLeft + offset;
        this.transition = true;
      }
      if(newLeft < -300) {
        this.toLeft = 0;
        this.transition = false;
      }
    },
    autoPlay() {
      this.timer = setInterval(function(){
        this.change(-100);
        this.circleFill(1);
      }.bind(this), 2500);
    },
    stop() {
      clearInterval(this.timer);
    },
    circleFill(x) {
      if (this.index < 3) {
        this.index += x;
      }
      else{
        this.index = 0;
      }
      for(let i = 0; i < this.circles.length; i++ ) {
        if(this.circles[i].fill == true) {
          this.circles[i].fill = false;
        }
      }
      this.circles[this.index].fill = true;
    },
    select(x) {
      this.toLeft = 0;
      this.change(-100 * x);
      this.index = 0;
      this.circleFill(x);
    }
  },
  mounted() {
    this.autoPlay();
  }
};

const images = [
  "/carousel_1.jpg",
  "/carousel_2.jpg",
  "/carousel_3.jpg",
  "/carousel_4.jpg"
]

const circles = [
  {
    id: 0,
    fill: true
  },
  {
    id: 1,
    fill: false
  },
  {
    id: 2,
    fill: false
  },
  {
    id: 3,
    fill: false
  }
]

</script>

<style lang="scss" scoped>

.carousel {
  background: linear-gradient(180deg, rgba( 0, 0, 0, .6), transparent);
  display: flex;
  width: 100%;
  height: 450px;
  position: relative;
  overflow: hidden;
  .images {
    min-width: 100%;
    height: 100%;
    position: relative;
    cursor: crosshair;
    overflow: hidden;
    img {
      display: block;
      min-width: 70%;
      height: 100%;
    }
    .img1 {
      opacity: .2;
    }
    .img2 {
      position: absolute;
      top: 0;
      right: 0;
      opacity: .2;
    }
    .img3 {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
    }
  }
  .circle-wrap {
    position: absolute;
    bottom: 5%;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    .circle {
      width: 10px;
      height: 10px;
      border: 1px solid #fff;
      border-radius: 50%;
      margin: 0 5px;
      cursor: pointer;
    }
    .circle-fill {
      background-color: #fff;
    }
  }
}
.transition {
  transition: left .8s ease-in-out;
}

@media screen and (max-width: 480px) {
  .carousel {
    height: calc(450px*.7);
  }
}

</style>

