<template>
  <div class="header-bgc">
    <div class="header">
      <router-link to="/"><div class="logo"></div></router-link>
      <div class="nav">
        <div class="philosophy">{{ philosophy }}</div>
        <div class="bars" :class="{invisible: !isTrue}" @click="toggle">
          <i class="fas fa-bars" ></i>
        </div>
        <div class="bars" :class="{invisible: isTrue}" @click="toggle">
          <i class="fas fa-times" ></i>
        </div>
        <div class="nav-item" :class="{invisible: isTrue}">
          <router-link to="/product">產品</router-link>
          <router-link to="/login">登入</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data(){
    return {
      philosophy: "能給人帶來幸福、溫暖、滿足、趣味的天然優質麵包",
      isTrue: true,
    }
  },
  methods: {
    toggle() {
      this.isTrue = !this.isTrue;
      console.log(this.isTrue);
    }
  }
};
</script>

<style lang="scss" scoped>
$bgc: rgba(255 ,255 ,255 , .5);
$bgc1: rgba(255 ,255 ,255 , .8);
$remark: rgba(180, 180, 180, 1);
$orange: rgba(247, 132, 37, 1);
$light_orange: rgba(250, 178, 119, 1);

.header-bgc {
  background: url(/nav.png) no-repeat top left;
  background-size: 256px;
  .header {
    position: absolute;
    max-width: 100%;
    height: 60px;
    background-color: $bgc;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 calc(100%/14);
    box-shadow: 0 0 6px 2px $bgc;
    position: relative;
    z-index: 1;
    .logo {
      position: absolute;
      top: -15px;
      left: -20px;
      width: 130px;
      height: 130px;
      border-radius: 50%;
      box-shadow: 0 0 10px $bgc;
      background: url(/logo.png) no-repeat center center;
      background-size: 135%;
      &:hover {
        box-shadow: 0 0 10px 3px $bgc;
        transition: .5s ease-in-out;
        transform: scale(1.05);
      }
    }
    .nav {
      display: flex;
      .philosophy {
        color: $remark;
        font-size: .8rem;
        font-style: italic;
        margin-right: 20px;
      }
      .nav-item {
        a {
          text-decoration: none;
          color: $orange;
          margin-left: 20px;
          &:hover {
            // background: linear-gradient(90deg, transparent, $light_orange, transparent) no-repeat;
            // background-position: bottom;
            // background-size: 100% 5%;
            color: $light_orange;
          }
        }
      }
      .bars {
        display: none;
      }
    }
  }
}

@media screen and (max-width: 768px) {
  .header-bgc {
    .header {
      .logo {
        top: -12px;
        left: -15px;
        width: 110px;
        height: 110px;
      }
      .nav {
        .philosophy {
          display: none;
        }
      }
    }
  }
}

@media screen and (max-width: 480px) {
  .header-bgc {
    background-position: -30px 6px;
    background-size: 220px;
    .header {
      padding: 0;
      height: 80px;
      .nav {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        width: 100%;
        height: 40%;
        .nav-item {
          background-color: $bgc1;
          width: 100%;
          margin-top: 20px;
          a {
            margin: 15px;
            display: block;
            text-align: end;
            &:hover {
              // background: none;
              color: $light_orange;
            }
          }
        }
        .bars {
          display: block;
          color: $orange;
          cursor: pointer;
          margin-right: 20px; 
          font-size: 1.2rem;
        }
        .invisible {
          display: none;
        }
      }
    }
  }
}

</style>

