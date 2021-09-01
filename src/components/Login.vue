
<template>
    <div class="login">
        <div class="login-top">
            <img class="login-top-img" src="/img/2.jpg" alt="">
        </div>
        <div class="fen"></div>
        <div class="login-con">
            <div class="login-con-phone">
                <input class="login-con-phone-input" type="text" placeholder="请输入手机号" v-model="value">
                <span class="login-con-phone-span" @click="huoqu" v-show="!show">{{txt}}</span>
            </div>
            <div class="login-con-duan" v-show="!show">
                <input class="login-con-duan-input" type="text" placeholder="请输入短信验证码" v-model="sms_code">
            </div>
            <div class="login-con-duan" v-show="show">
                <input class="login-con-duan-input" type="text" placeholder="请输入密码" v-model="password">
            </div>
            <div class="login-con-wei">
                <span v-show="!show">*未注册的手机号将自动注册</span>
                <span v-show="show" @click="zhao">找回密码</span>
                <span @click="show=true" v-show="!show">使用密码登录</span>
                <span @click="show=false" v-show="show">注册/验证码登录</span>
            </div>
            <div class="login-con-login">
                <p class="login-con-login-p" v-show="!show" @click="login">登 录</p>
                <p class="login-con-login-p" v-show="show" @click="logini">登 录</p>
                <p class="login-con-login-xieyi">
                    <img class="login-con-login-xieyi-img" src="/img/05.png" alt="">
                    我同意<span class="login-con-login-xieyi-span">用户注册协议</span>
                    和<span class="login-con-login-xieyi-span">隐私保护协议</span>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import { smsCode, login } from "@/http/api";
export default {
  data() {
    return {
      txt: "获取验证码",
      value: "",
      sms_code: "",
      password: "",
      show:false
    };
  },
  created() {},
  methods: {
    // 获取验证
    async huoqu() {
      var phoneReg = /^[1]([3-9])[0-9]{9}$/;
      if (!phoneReg.test(this.value)) {
        return this.$toast({
          message: "手机号格式不正确"
        });
      } else {
        var obj = { mobile: this.value, sms_type: "login" };
        let res = await smsCode(obj);
        console.log(res);
      }
      this.getSecond(60);
    },
    // 时间
    getSecond(wait) {
      let _this = this;
      let _wait = wait;
      if (wait == 0) {
        this.btnDisabled = false;
        this.txt = "获取验证码";
        wait = _wait;
      } else {
        this.btnDisabled = true;
        this.txt = "验证码(" + wait + "s)";
        wait--;
        setTimeout(function() {
          _this.getSecond(wait);
        }, 1000);
      }
    },
    // 登录短信
    async login() {
      if(this.value=="" && this.sms_code==""){
        alert("内容不能为空")
        return false
      }
      let res = await login({ mobile: this.value, sms_code: this.sms_code , client:"1",	type:2,});
      console.log(res);
      if(res.data.code==200){
        this.$router.push("/My")
      }
    },
    // 登录密码
     async logini() {
      if(this.value=="" && this.sms_code==""){
        alert("内容不能为空")
        return false
      }
      let res = await login({ mobile: this.value,password:this.password , client:"1",	type:1,});
      console.log(res);
        if(res.status==200){
          this.$router.push('/My')
        }
        this.$store.commit("token",res.data.data.remember_token)
        this.$store.commit("zhang",res.data.data.nickname)
    },

    zhao(){
      this.$router.push("/zhao")
    }
  }
};
</script>

<style lang="scss">
.login {
  width: 375px;
  height: auto;
}
.login-top {
  margin-top: 10px;
  width: 375px;
  height: 255px;
  .login-top-img {
    width: 100%;
    height: 100%;
  }
}

.fen {
  margin-top: 20px;
  width: 375px;
  height: 20px;
  background: rgb(221, 220, 220);
}
.login-con {
  width: 375px;
  height: 130px;
  .login-con-phone {
    width: 300px;
    line-height: 50px;
    background: #fff;
    border-bottom: 1px solid #f1f1f1;
    margin-left: 30px;
    margin-top: 50px;
    .login-con-phone-input {
      border: 0;
      font-size: 15px;
    }
    .login-con-phone-span {
      display: inline-block;
      margin-right: 0;
      margin-left: 40px;
      color: #f00;
    }
  }
  .login-con-duan {
    width: 300px;
    line-height: 50px;
    background: #fff;
    border-bottom: 1px solid #f1f1f1;
    margin-left: 30px;
    .login-con-duan-input {
      border: 0;
      font-size: 15px;
    }
  }
  .login-con-wei {
    width: 300px;
    display: flex;
    justify-content: space-between;
    margin-left: 30px;
    margin-top: 10px;
    color: #b7b7b7;
  }
  .login-con-login {
    width: 375px;
    height: 187px;
    background-image: url("/img/03.png");
    background-size: 100%;
    .login-con-login-p {
      padding-left: 165px;
      padding-top: 70px;
      font-size: 14px;
      color: #fff;
    }
    .login-con-login-xieyi {
      width: 300px;
      line-height: 20px;
      margin-left: 40px;
      margin-top: 30px;
      .login-con-login-xieyi-img {
        width: 15px;
        height: 15px;
      }
      .login-con-login-xieyi-span {
        color: #f00;
      }
    }
  }
}
</style>
