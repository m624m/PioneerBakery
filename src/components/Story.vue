<template>
  <div class="story">
    <div class="title" @mouseover="mouseOn">
      <h3>{{ story.title }}</h3>
    </div>
    <div class="info" :class="[{invisible: isVisible},{appear: isAppear}]">
      <div class="info-wrap">
        <div><img :src="story.img"></div>
        <p v-html="story.info"></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Story",
  props: {
    story: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      isVisible: true,
      isAppear: false,
    }
  },
  methods: {
    handleScroll(event) {
      if (window.scrollY > 0) {
        this.isVisible = false;
        this.isAppear = true;
      }
    },
    mouseOn() {
      this.isVisible = false;
      this.isAppear = true;
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
    console.log("created");
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
    console.log("beforeDestory");
  }
};

</script>

<style lang="scss" scoped>
$bgc: rgba(255, 255, 255, .7);
$bgc1: rgba(255, 255, 255, .4);
$orange: rgba(247, 132, 37, 1);
$brown: rgba(170, 147, 127, 0.3);

.story {
  text-align: center;
  .title {
    color: $orange;
    background-color: $bgc;
    border-radius: 0 0 30px 30px;
    height: 4rem;
    position: relative;
    z-index: 1;
    box-shadow: 0 -2px 4px $orange inset;
    h3 {
      margin: 0;
      line-height: 4rem;
      vertical-align: middle;
      letter-spacing: .5rem;
      font-weight: 300;
    }
  }
  .info {
    .info-wrap {
      max-width: 70%;
      box-sizing: border-box;
      margin: 0 auto;
      padding-right: calc(100vw/10);
      background: linear-gradient(90deg, $brown, transparent);
      box-shadow: 0 0 10px 10px $bgc;
      position: relative;
      div {
        padding-right: calc(100vw/8);
      }
      img {
        width: 100%;
        height: 100%;
        opacity: .3;
        vertical-align: top;
      }
      p {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate( -40%, -50%);
        background-color: $bgc1;
        box-sizing: border-box;
        padding: calc(100vw/30);
        margin: 0;
        width: 75%;
        font-size: calc(1.5*100vw/100);
        line-height: calc(2*100vw/100);
      }
    }
  }
}

.invisible {
  display: none;
}

.appear {
  animation: fadein 2s linear;
}

@keyframes fadein {
  0% {opacity: 0;}
  100% {opacity: 1;}
}


@media screen and (max-width: 768px) {
  .story {
    .title {
      height: 5rem;
      h3 {
        line-height: 5rem;
      }
    }
    .info {
      .info-wrap {
        max-width: 80%;
        padding: 0;
        display: flex;
        flex-direction: column;
        background: transparent;
        div {
          padding: 0;
          width: 100%;
        }
        p {
          width: 100%;
          background-color: transparent;
          position: static;
          transform: none;
          font-size: .8rem;
          line-height: 1.5rem;
          padding: calc(100vw/10);
        }
      }
    }
  }
}

</style>

