<template>
    <div class="my" >
        <div class="my-top">
            <div v-show="$store.state.token==''">
                <p class="my-top-img"><img class="my-top-img-img" src="/img/02.png" alt=""></p>
                <p class="my-top-p" @click="login">登录/注册</p>
            </div>
            <div v-show="$store.state.token!=''">
                <p class="my-top-img"><img class="my-top-img-img" src="/img/02.png" alt=""></p>
                <p class="my-top-p">{{$store.state.zhang}}</p>
            </div>
            <div  v-show="$store.state.token!=''" class="my-top-qian" @click="qian">
                <span><img  class="my-wo-ul-li-img" src="/img/22.png" alt=""></span>
                <span class="my-wo-ul-li-i">签到</span>
            </div>
            <div class="my-top-xue">
                <ul class="my-top-xue-ul">
                    <li class="my-top-xue-ul-li">
                        <p class="my-top-xue-ul-li-p">0</p>
                        <p class="my-top-xue-ul-li-p2">我的学习</p>
                    </li>
                    <li class="my-top-xue-ul-li">
                        <p class="my-top-xue-ul-li-p3">0</p>
                        <p class="my-top-xue-ul-li-p2">本周课时</p>
                    </li>
                    <li class="my-top-xue-ul-li">
                        <p class="my-top-xue-ul-li-p3">0</p>
                        <p class="my-top-xue-ul-li-p2">我的积分</p>
                    </li>
                </ul>
            </div>
        </div>
        <div class="my-hui"></div>
        <div class="my-wo">
            <ul class="my-wo-ul">
                <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/22.png" alt=""></span>
                    <span class="my-wo-ul-li-i">我的作业</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/23.png" alt=""></span>
                    <span class="my-wo-ul-li-i">我的社区</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
            </ul>
        </div>
         <div class="my-hui"></div>
        <div class="my-wo">
            <ul class="my-wo-ul">
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/23.png" alt=""></span>
                    <span class="my-wo-ul-li-i">订单管理</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/24.png" alt=""></span>
                    <span class="my-wo-ul-li-i">图书管理</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
            </ul>
        </div>
        <div class="my-hui"></div>
        <div class="my-wo">
            <ul class="my-wo-ul">
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/23.png" alt=""></span>
                    <span class="my-wo-ul-li-i">一优惠卷</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/24.png" alt=""></span>
                    <span class="my-wo-ul-li-i">学习号卡</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/25.png" alt=""></span>
                    <span class="my-wo-ul-li-i">分销中心</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
            </ul>
        </div>
        <div class="my-hui"></div>
        <div class="my-wo">
            <ul class="my-wo-ul">
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/23.png" alt=""></span>
                    <span class="my-wo-ul-li-i">消息中心</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/24.png" alt=""></span>
                    <span class="my-wo-ul-li-i">地址管理</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/25.png" alt=""></span>
                    <span class="my-wo-ul-li-i">关于我们</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li">
                    <span><img  class="my-wo-ul-li-img" src="/img/25.png" alt=""></span>
                    <span class="my-wo-ul-li-i">意见反馈</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
                 <li class="my-wo-ul-li" @click="zhao">
                    <span><img  class="my-wo-ul-li-img" src="/img/25.png" alt=""></span>
                    <span class="my-wo-ul-li-i">设置</span>
                    <span class="my-wo-ul-li-im">></span>
                </li>
            </ul>
        </div>
        <div class="my-hui2"></div>
    </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
    login() {
      this.$router.push("/login");
    },
    zhao() {
      if (this.$store.state.token == "") {
        this.$router.push("/Login");
      } else {
        this.$router.push("/she");
      }
    },
    qian(){
        this.$router.push('/qian')
    }
  }
};
</script>
<style lang="scss">
.my {
  width: 100%;
  height: auto;
}
.my-top {
  width: 375px;
  height: 300px;
  background-image: url("/img/01.png") !important;
  background-repeat: no-repeat;
  background-size: 100%;
  text-align: center;
  position: relative;
  .my-top-img {
    width: 60px;
    height: 60px;
    margin-left: 155px;
    padding-top: 50px;
    .my-top-img-img {
      width: 100%;
      height: 100%;
    }
  }
  .my-top-p {
    width: 100%;
    text-align: center;
    font-size: 18px;
    color: #fff;
    margin-top: 10px;
  }
  .my-top-xue {
    width: 100%;
    height: 75px;
    .my-top-xue-ul {
      width: 100%;
      margin-top: 80px;
      text-align: center;
      list-style: none;
      .my-top-xue-ul-li {
        float: left;
        margin-left: 45px;
        height: 75px;
        font-size: 17px;
        .my-top-xue-ul-li-p {
          color: deepskyblue;
          font-size: 20px;
        }
        .my-top-xue-ul-li-p2 {
          margin-top: 7px;
        }
        .my-top-xue-ul-li-p3 {
          color: red;
          font-size: 20px;
        }
      }
    }
  }
}
.my-hui {
  width: 100%;
  height: 10px;
  background: #d3d0d0;
}
.my-wo {
  width: 100%;
  .my-wo-ul {
    width: 100%;
    list-style: none;
    background: #d3d0d0;
    .my-wo-ul-li {
      width: 100%;
      // height: 56px;
      background: white;
      margin-top: 1px;
      align-content: center;
      line-height: 56px;
      position: relative;
      .my-wo-ul-li-img {
        width: 15px;
        height: 14px;
      }
      .my-wo-ul-li-i {
        margin-left: 5px;
        font-size: 15px;
      }
      .my-wo-ul-li-im {
        font-size: 20px;
        position: absolute;
        top: 0;
        right: 20px;
      }
    }
  }
}
.my-hui2 {
  width: 100%;
  height: 80px;
  background: #d3d0d0;
}
.my-top-qian {
  width: 60px;
  height: 20px;
  text-align: center;
  background: deepskyblue;
  position: absolute;
  top: 80px;
  left: 315px;
  border-radius: 10px 0 0 10px;
  .my-wo-ul-li-img {
    width: 15px;
    height: 14px;
  }
  .my-wo-ul-li-i {
    margin-left: 5px;
    font-size: 10px;
    color: white;
  }
}
</style>
