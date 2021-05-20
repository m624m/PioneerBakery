<template>
  <div class="login">
    <div class="login-wrap">
      <div class="main-label">
        <div :class="{'label-active': login}" @click="switchPage(0)">登入</div>
        <div :class="{'label-active': !login}" @click="switchPage(1)">註冊</div>
      </div>
      <form name="login" method="post" action="#" :class="{invisible: !login}">
        <p>帳號</p>
        <input type="text" class="input" name="username" required>
        <p>密碼</p>
        <input type="password" class="input" name="password" required>
        <input type="checkbox" id="keep" name="keep-login" class="keep-checkbox" checked>
        <label for="keep" class="keep-label">保持登入狀態</label>
        <input type="submit" class="submit" value="登入">
        <div class="forget"><a href="#">忘記密碼?</a></div>
      </form>
      <form name="signup" method="post" action="#" :class="{invisible: login}">
        <p>帳號</p>
        <input type="text" class="input" name="username" required>
        <p>密碼</p>
        <input type="password" class="input" name="password" required>
        <p>確認密碼</p>
        <input type="password" class="input" name="password" required>
        <p>信箱</p>
        <input type="email" class="input" required>
        <input type="submit" class="submit" value="註冊">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "LoginView",
  data() {
    return {
      login: true,
    }
  },
  methods: {
    switchPage(x) {
      if(x == 0) {
        this.login = true;
      }
      if(x == 1) {
        this.login = false;
      }
    }
  }
};

</script>

<style lang="scss" scoped>
$bgc: rgba(255, 238, 223, 1);
$bgc1: rgba(255 ,255 ,255 , .8);
$remark: rgba(180, 180, 180, 1);
$remark1: rgba(180, 180, 180, .2);
$orange: rgba(247, 132, 37, 1);

@mixin border {
  width: 100%;
  box-sizing: border-box;
  border: none;
  font-size: .8rem;
  padding: 10px;
  border-radius: 10px;
  margin: 10px 0;
}

.invisible {
  display: none;
}

.login {
  background-color: $bgc;
  border: transparent solid;
}

.label-active {
  border-bottom: 2px double $orange;
  font-weight: 600;
}

.login-wrap {
  box-sizing: border-box;
  max-width: 350px;
  margin: 50px auto;
  padding: 50px;
  background-color: $bgc1;
  border-radius: 10px;
  .main-label {
    display: flex;
    div {
      margin-right: 10px;
      font-size: 1.2rem;
      line-height: 2rem;
      color: $orange;
      cursor: pointer;
    }
  }
  form {
    color: $remark;
    margin: 20px 0;
    .input {
      @include border;
      background-color: $remark1;
      &:focus {
        outline: none;
      }
    }
    p {
      margin: 10px 0 0;
      line-height: 1rem;
    }
    .keep-checkbox {
      vertical-align: middle;
    }
    .keep-label {
      font-size: .6rem;
    }
    .submit {
      @include border;
      background-color: $orange;
      color: #fff;
      cursor: pointer;
    }
    .forget {
      font-size: .6rem;
      width: 100%;
      text-align: center;
      a {
        text-decoration: none;
        color: $remark;
      }
    }
  }
}

</style>
