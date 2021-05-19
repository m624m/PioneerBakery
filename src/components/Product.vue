<template>
  <div class="product">
    <h2>{{ chosenBread.type }}</h2>
    <div class="item" v-for="item in chosenBread.flavors" :key="item.id">
      <img :src="item.image" :alt="item.name">
      <div class="intro">
        <div class="intro-title">
          <h3>{{ item.name }}</h3>
          <h4>$ {{ item.price }}</h4>
        </div>
        <p>{{ item.intro }}</p>
      </div>
      <i class="fas fa-shopping-cart"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: {
    chosenBread: {
      type: Object,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
$bgc: rgba(255 ,255 ,255 , .5);
$remark: rgba(90, 90, 90, 1);
$orange: rgba(247, 132, 37, 1);
$light_orange: rgba(250, 178, 119, 1);

* {
  margin: 0;
}

.product {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  h2 {
    width: 90%;
    color: $light_orange;
    text-align: center;
    margin-bottom: 20px;
    // background-color: $bgc;
    // padding: 20px 0;
    // border-top-left-radius: 20px;
    // border-top-right-radius: 20px;
  }
}

.item {
  display: flex;
  align-items: center;
  margin: 20px;
  img {
    width: 120px;
    height: 120px;
    margin-right: 10px;
  }
  .intro {
    color: $remark;
    width: 250px;
    .intro-title {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    h3 {
      color: $orange;
    }
    h4 {
      color: $light_orange;
      margin-right: 20px;
    }
    p {
      font-size: .8rem;
    }
  }
  .fa-shopping-cart {
    color: $orange;
    cursor: pointer;
    padding: 0 10px;
  }
}

@media screen and (max-width: 480px) {
  .product {
    h2 {
      margin: 0;
    }
  }
  .item {
    flex-direction: column;
    img {
      width: 200px;
      height: 200px;
    }
    .fa-shopping-cart {
      padding: 10px;
      margin-top: 10px;
      width: 90%;
      border-radius: 10px;
      background-color: $bgc;
    }
  }
}

</style>