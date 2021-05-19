<template>
  <div class="category">
    <div class="title">麵包類別</div>
    <ul>
      <li
        v-for="bread in bread" 
        :key="bread.id"
        @click="filter(bread.id)"
      >
      {{ bread.type }} <span>({{ bread.products }})</span></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ProductCategory",
  props: {
    bread: {
        type: Array,
        required: true,
    }
  },
  methods: {
    filter(id) {
      this.$emit("filter",id);
    }
  }
};
</script>

<style lang="scss" scoped>
$bgc: rgba(255 ,255 ,255 , .6);
$orange: rgba(247, 132, 37, 1);
$light_orange: rgba(250, 178, 119, 1);

* {
  margin: 0;
  padding: 0;
  list-style: none;
}

.category {
  border: solid transparent;
  text-align: center;
  color: $orange;
  min-width: 160px;
  margin-right: 20px;
  .title {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    background-color: $light_orange;
    color: #fff;
    padding: 10px;
  }
  ul {
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    background-color: $bgc;
    padding: 10px 0;
  }
  li {
    cursor: pointer;
    padding: 5px 20px;
    &:hover {
      color: $light_orange;
    }
    span {
      font-size: .7rem;
    }
  }
}

@media screen and (max-width: 768px) {
  .category {
    margin-right: 0;
    margin-bottom: 50px;
    ul {
      display: flex;
      justify-content: center;
    }
  }
}

</style>