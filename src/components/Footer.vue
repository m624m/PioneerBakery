<template>
  <div class="footer">
    <div class="about">
      <h3>拓荒小麥</h3>
      <p>{{ feature }}</p>
    </div>
    <div class="other">
      <img src="/images/cat.png" alt="Logo">
      <p>
        地址 <span>{{ contact.add }}</span><br>
        電話 <span>{{ contact.phone }}</span><br>
        信箱 <span>{{ contact.email }}</span>
      </p>
      <div class="right">
        <div class="social-media">           
          <a href="#"><i class="fab fa-twitter-square" style="color:#00ACEE"></i></a>
          <a href="#"><i class="fab fa-facebook-square" style="color:#3b5998"></i></a>
          <a href="#"><i class="fab fa-instagram-square" style="color:#D33187"></i></a>
        </div>
        <div class="copy-right">拓荒小麥 2021 &copy; All Rignts Reserved</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    contact: {
      type: Object,
    }
  },
  data() {
    return {
      feature: "無油、低糖、低鹽，天然無添加貝果。希望將許多人對貝果的既定印象改變，不再是乾硬，而是有嚼勁、Q軟彈性，老少都可接受。",
    }
  }
};
</script>

<style lang="scss" scoped>
$bgc: rgba(255 ,255 ,255 , .5);
$remark: rgba(180, 180, 180, 1);
$orange: rgba(247, 132, 37, 1);
$blue: rgba(37, 152, 247, .4);

%ml {
  margin-left: 20px;
}

.footer {
  max-width: 100%;
  background-color: $bgc;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 calc(100%/14);
  box-shadow: 0 0 6px 2px $bgc;
  color: $orange;
  .about {
    width: calc(100%*3/10);
    h3 {
      margin-bottom: 0;
    }
    p {
      margin-top: 0;
    }
  }
  p {
    font-size: .7rem;
    line-height: 1.2rem;
    color: $remark;
  }
  .other {
    display: flex;
    img {
      @extend %ml;
      width: 120px;
      height: 120px;
    }
    p {
      @extend %ml;
      align-self: center;
      span {
      border-bottom: 1px solid $remark;
    }
    }
    .right {
      @extend %ml;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: flex-end;
      a {
        font-size: 1.4rem;
        margin: 3px;
      }
    }
    .copy-right {
      color: $remark;
      font-size: .5rem;
      font-family: sans-serif;
      letter-spacing: 0;
    }
  }
}

@media screen and (max-width: 768px) {
  .footer {
    flex-direction: column;
    padding-bottom: 10px;
    .about {
      width: 100%;
    }
    .other {
      width: 100%;
      margin-left: -30px;
      flex-wrap: wrap;
      img {
        box-shadow: 0 0 10px $blue inset;
        border-radius: 50%;
      }
      .right {
        margin-top: 20px;
        width: 100%;
      }
    }
  }
}

</style>

