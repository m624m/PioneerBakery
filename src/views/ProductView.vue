<template>
  <div class="product-view">
    <ProductCategory :bread="bread" @filter="filter"></ProductCategory>
    <Product :chosenBread="chosenBread[0]"></Product>
  </div>
</template>

<script>
import ProductCategory from "@/components/ProductCategory.vue";
import Product from "@/components/Product.vue";

export default {
  name: "ProductView",
  components: {
    ProductCategory,
    Product
  },
  data() {
    return {
      bread: bread,
      chosenBread: bread
    }
  },
  methods: {
    filter(id) {
      this.chosenBread = this.bread.filter(element => element.id == id);
    }
  }
};

const bread= [
  {
    id: 0,
    type: "貝果",
    products: 6,
    flavors: [
      {
        name: "經典原味",
        image: "/images/bagel_0.png",
        price: 35,
        intro: "單純小麥香，越嚼越香，適合搭配自己喜愛的餡料。",
      },
      {
        name: "黑糖核桃",
        image: "/images/bagel_1.png",
        price: 40,
        intro: "手炒融化的黑糖與烤過的核桃香氣濃厚。",
      },
      {
        name: "檸檬可可",
        image: "/images/bagel_2.png",
        price: 45,
        intro: "60%微甜不膩的可可，與檸檬皮丁後韻的滋味點綴。",
      },
      {
        name: "清爽藍莓",
        image: "/images/bagel_3.png",
        price: 55,
        intro: "野生小藍莓打入麵團增添風味與著色，內餡包裹大顆藍莓果乾，爽口多汁。",
      },
      {
        name: "剝皮辣椒乳酪",
        image: "/images/bagel_4.png",
        price: 50,
        intro: "微鹹微辣的剝皮辣椒，搭配淡淡果香的濃郁乳酪，特殊風味意外絕配！",
      },
      {
        name: "杏仁可可",
        image: "/images/bagel_5.png",
        price: 50,
        intro: "64%苦甜調溫可可口感滑順，與帶有顆粒感的杏仁角。",
      }
    ]
  },
  {
    id: 1,
    type: "湯種吐司",
    products: 2,
    flavors: [
      {
        name: "原味湯種",
        image: "/images/toast_0.png",
        price: 70,
        intro: "挑選獨特麥香的麵粉製作，能嘗到淡淡的自然麥香及甜味，口感較軟卻不失扎實。",
      },
      {
        name: "玫瑰湯種",
        image: "/images/toast_1.png",
        price: 85,
        intro: "除了淡淡的自然麥香及甜味，加入玫瑰增添優雅香氣。",
      }
    ]
  },
  {
    id: 2,
    type: "小歐法",
    products: 2,
    flavors: [
      {
        name: "伯爵南瓜子",
        image: "/images/euro_0.png",
        price: 50,
        intro: "伯爵紅茶香氣十足，搭配南瓜子堅果，口齒留香。",
      },
      {
        name: "萊姆莓果",
        image: "/images/euro_1.png",
        price: 50,
        intro: "麵團以萊姆酒為基底，混多種莓果，滋味豐富。",
      }
    ]
  }
]

</script>

<style lang="scss" scoped>
$bgc: rgba(255, 238, 223, 1);

.product-view {
  background-color: $bgc;
  border: transparent solid;
  max-width: 100%;
  display: flex;
  padding: 50px;
}

@media screen and (max-width: 768px) {
  .product-view {
    padding: 20px;
    flex-direction: column;
  }
}

</style>
