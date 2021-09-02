<template>
    <div class="zjx">
        <!-- 图片 -->
        <div class="zjx-img">
            <img :src="list.info.cover_img" alt="">
        </div>
        <!-- 介绍 -->
        <div class="zjx-jie">
            <div class="zjx-jie-d">
                <p class="zjx-jie-shao">{{list.info.address}}</p>
                <p>剩余名额：{{list.info.stock}}</p>
                <p>报名截止时间：2021.07.15 00:00</p>
                <p>开课时间：2021/07/05 00:00 - 2021/07/06 00:00</p>
                <p>开课地点：北京东城区少林武馆</p>
                <p class="zjx-jie-yi">100</p>
            </div>
        </div>
        <div class="hui"></div>
        <!-- 优惠 -->
        <div class="zjx-yh">
          <p>
            <van-cell is-link title="优惠：领取优惠卷最多可以件减80" @click="show = true" />
                <van-action-sheet v-model="show" title="标题">
                <div class="content">内容</div>
            </van-action-sheet>
          </p>
          <p>
              <van-cell is-link title="服务：课程售后" @click="show = true" />
                <van-action-sheet v-model="show" title="标题">
                <div class="content">内容</div>
              </van-action-sheet>
          </p>
        </div>
        <div class="hui"></div>
        <!-- 教学团队 -->
        <div class="zjx-jiao">
            <div class="zjx-jiao-img"  v-for="item in lists" :key="item.id">
                <img @click="go(item.id)" :src="item.avatar" alt="">
                 <p class="zjx-jiao-xing">
                {{item.teacher_name}}
                </p>
            </div>
           
        </div>
        <div class="hui"></div>
        <!-- 课程介绍 -->
        <div class="zxj-ke">
            <van-tabs v-model="active">
                <van-tab title="课程介绍">
                    <div v-html="list.info.course_details"> </div>
                </van-tab>
                <van-tab title="课程大纲">  <div v-html="list.info.course_details"> </div></van-tab>
                <van-tab title="课程评论"> <div v-html="list.info.course_details"> </div></van-tab>
            </van-tabs>
             <div class="hui"></div>
             <div class="zxj-ke-da">
                 <p>课程大纲</p>
                    <van-collapse v-model="activeNames">
                     <van-collapse-item title="1. 站马步" name="1">站马步</van-collapse-item>
                    </van-collapse>
             </div>
             <div class="hui"></div>
            <div class="zxj-ke-ping">
                <p>课程评论</p>
                <img src="/img/333.png" alt="">
            </div>
        </div>
        <!-- 按钮 -->
        <div class="zxj-btn">
            <button>立刻报名</button>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      id: 0,
      list: [],
      show: false,
      lists: [],
      active: 0,
      activeNames:['1']
    };
  },
  created() {
    this.id = this.$route.query.id;
    // console.log(this.id)
    this.getlist();
  },
  methods: {
    async getlist() {
      let { data: res } = await this.$http.get(
        "http://120.53.31.103:84/api/app/courseInfo/basis_id=" + this.id + "?"
      );
      console.log(res);
      this.list = res.data;
      this.lists = res.data.teachers;
    },
    onSelect(item) {
      this.show = false;
      Toast(item.name);
    },
    go(id){
      this.$router.push({
                path:"/kxiang",
                query:{
                    id:id
             }
        })
    }
  }
};
</script>
<style lang="scss">
.zjx {
  width: 100vw;
  height: 100%;
  position: relative;
  .zjx-img {
    width: 100%;
    height: 214px;
    background: #e6e4e4;
    img {
      width: 50%;
      height: 100%;
    }
  }
  .zjx-jie {
    width: 100%;
    height: 187.5px;
    .zjx-jie-d {
      margin-left: 10px;
      margin-top: 10px;
    }
    p {
      font-size: 15px;
      color: #999999;
      margin-top: 10px;
    }
    .zjx-jie-shao {
      font-size: 20px;
      color: black;
    }
    .zjx-jie-yi {
      font-size: 20px;
      color: red;
    }
  }
  .zjx-jiao {
    width: 100%;
    height: 200px;
    .zjx-jiao-img {
      width: 60px;
      height: 60px;
      text-align: center;
      margin-left: 20px;
      margin-top: 15px;
      float: left;
      img {
        width: 50px;
        height: 50px;
        border-radius: 25px;
        // border: 1px solid black;
      }
    }
  }
}
.content {
  padding: 16px 16px 160px;
}
.hui {
  width: 100%;
  height: 10px;
  background: #e6e4e4;
}
.zxj-ke {
  width: 100%;
  .van-tabs {
    width: 100%;
    height: 200px;
    div {
      font-size: 15px;
      p {
        margin-top: 10px;
      }
    }
  }
  .zxj-ke-da{
      width: 100%;
      height: 120px;
      p{
          font-size: 18px;
      }
      .van-collapse-item{
          font-size: 15px;
      }
  }
  .zxj-ke-ping{
      width: 100%;
      height: 300px;
      p{
          font-size: 18px;
      }
      img{
          width: 150px;
          height: 150px;
          margin-top: 30px;
          margin-left: 150px
      }
    }
}
.zxj-btn{
    width: 100%;
    height: 50px;
    position: fixed;
    bottom: 0;
    left: 0;
    button{
        width: 80%;
        height: 40px;
        color: white;
        border: 1px solid red;
        border-radius: 20px;
        background: red;
        margin-left: 10%;
        margin-top: 5px;
    }
}
</style>


