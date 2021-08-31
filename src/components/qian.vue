<template>
    <div class="qian">
        <!-- 用户 -->
        <div class="qian-shang">
            <div class="qian-shang-tou">
                <div class="qian-shang-tou-img">
                    <img class="qian-shang-tou-img-img" src="/img/02.png" alt="">
                </div>
                <div class="qian-shang-tou-shou">
                    <p class="qian-shang-tou-shou-h">{{$store.state.zhang}}</p>
                    <p class="qian-shang-tou-shou-f">积分：6</p>
                </div>
                <div class="qian-shang-tou-cha">
                   签到规则
                </div>
            </div>
        </div>
        <!-- 日期 -->
        <div class="qian-ri">
           <van-calendar
                :poppable="false"
                :show-confirm="false"
                :style="{ height: '340px' }"
                :row-height="40"
                @click="select"
                />
        </div>
        <!-- 推荐 -->
        <div class="qian-ke">
            <div class="qian-ke-s">
                 <div class="qian-ke-left">
                    <span class="qian-ke-left-span"></span>
                    <p class="qian-ke-left-p">好课推荐</p>
                </div>
                <div class="qian-ke-right">
                    <span class="qian-ke-right-span">更多</span>
                    <img class="qian-ke-right-img" src="/img/14.png" alt="">
                </div>
            </div>
               <van-card
                    num="2"
                    desc="论渣男"
                    title="1积分"
                    thumb="/img/3.jpg"
                    />
                    
        </div>
          <div class="qian-kel">
            <div class="qian-ke-s">
                 <div class="qian-ke-left">
                    <span class="qian-ke-left-span"></span>
                    <p class="qian-ke-left-p">热门图书</p>
                </div>
                <div class="qian-ke-right">
                    <span class="qian-ke-right-span">更多</span>
                    <img class="qian-ke-right-img" src="/img/14.png" alt="">
                </div>
            </div>
               <van-card
                    num="2"
                    desc="VUE后台"
                    title="1积分"
                    thumb="/img/4.jpg"
                    />
                    
        </div>
    </div>
    
</template>
<script>
export default {
  data() {
    return {};
  },
  methods: {
     
  }
};
</script>
<style lang="scss">
.qian {
  width: 100%;
  height: 100vh;
  // background: red;
  position: relative;
}
//  用户
.qian-shang {
  width: 100%;
  height: 280px;
  position: relative;
  background: red;
  .qian-shang-tou {
    width: 335px;
    height: 104px;
    position: absolute;
    top: 30px;
    left: 20px;
    .qian-shang-tou-img {
      width: 44px;
      height: 44px;
      float: left;
      .qian-shang-tou-img-img {
        width: 100%;
        height: 100%;
      }
    }
    .qian-shang-tou-shou {
      color: white;
      float: left;
      .qian-shang-tou-shou-h {
        font-size: 20px;
      }
      .qian-shang-tou-shou-f {
        font-size: 15px;
      }
    }
    .qian-shang-tou-cha {
      width: 76px;
      height: 22px;
      text-align: center;
      margin-top: 10px;
      float: left;
      background: red;
      color: black;
      font-size: 14px;
      color: white;
      border: 1px solid white;
      margin-left: 80px;
      border-radius: 11px;
    }
  }
}
//  日期
.qian-ri {
  width: 80%;
  height: 340px;
  border: 1px solid black;
  border-radius: 10%;
  position: absolute;
  top: 120px;
  left: 35px;
  .van-calendar {
    width: 100%;
    height: 100%;
    border-radius: 10%;
  }
}
// 推荐课
.qian-ke {
  width: 375px;
    position: absolute;
    top: 500px;
  .qian-ke-s {
    width: 375px;
    display: flex;
    justify-content: space-around;
   
    .qian-ke-left {
      width: 200px;
      // height: 16px;
      line-height: 16px;
      display: flex;
      .qian-ke-left-span {
        display: inline-block;
        width: 3px;
        height: 16px;
        font-size: 15px;
        background: #f00;
      }
      .qian-ke-left-p {
        font-size: 15px;
      }
    }
    .qian-ke-right {
      width: 90px;
      line-height: 16px;
      text-align: right;
      .qian-ke-right-span {
        font-size: 14px;
        display: inline-block;
        margin-right: 5px;
      }
      .qian-ke-right-img {
        width: 9px;
        height: 13px;
      }
    }
    .qian-ke-ke {
      width: 80%;
      height: 100px;
      .qian-ke-ke-img {
        width: 100px;
        height: 60px;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
  }
  .van-card{
      width: 350px;
      position: absolute;
      top:20px;
      left: 10px;
  }
}
.qian-kel {
  width: 375px;
    position: absolute;
    top: 650px;
  .qian-ke-s {
    width: 375px;
    display: flex;
    justify-content: space-around;
   
    .qian-ke-left {
      width: 200px;
      // height: 16px;
      line-height: 16px;
      display: flex;
      .qian-ke-left-span {
        display: inline-block;
        width: 3px;
        height: 16px;
        font-size: 15px;
        background: #f00;
      }
      .qian-ke-left-p {
        font-size: 15px;
      }
    }
    .qian-ke-right {
      width: 90px;
      line-height: 16px;
      text-align: right;
      .qian-ke-right-span {
        font-size: 14px;
        display: inline-block;
        margin-right: 5px;
      }
      .qian-ke-right-img {
        width: 9px;
        height: 13px;
      }
    }
    .qian-ke-ke {
      width: 80%;
      height: 100px;
      .qian-ke-ke-img {
        width: 100px;
        height: 60px;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
  }
  .van-card{
      width: 350px;
      position: absolute;
      top:20px;
      left: 10px;
  }
}
</style>


