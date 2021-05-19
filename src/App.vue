<template>
  <div id="app">
    <Header></Header>
    <router-view></router-view>
    <Footer :contact="contact"></Footer>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

export default {
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      contact: contact,
    }
  }
};

const contact = {
  add: "基隆市暖暖區快樂里12巷12號之12",
  phone: "02-1234567",
  email: "happy@gmail.com"
}

</script>


<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300&family=Rakkas&display=swap");

html, body {
  margin: 0;
  padding: 0;
  font-family: "Rakkas", "Noto Sans TC", sans-serif;
  font-size: 20px;
  line-height: 1.5rem;
  letter-spacing: 1.5px;
  color: rgba(75, 46, 21, 1);
}

</style>
