<template>

        <div class="kxiang" >
         <div class="kxiang-shang">
            <div class="kxiang-shang-tou" >
                <img  class="kxiang-shang-tou-img" :src="list.avatar" />
            </div>
            <div  class="kxiang-shang-name">
                {{list.real_name}}
            </div>
        </div>
        <div class="kxiang-xia">
             <van-tabs v-model="active">
                <van-tab class="kxiang-xia-yi" title="讲师介绍">
                    <p class="kxiang-xia-yi-lao">老师简介</p>
                    <p class="kxiang-xia-yi-xiao">{{list.introduction}}</p>
                </van-tab>
                <van-tab class="kxiang-xia-er" title="主讲课程">
                    <van-card
                    v-for="item in lists" :key="item.id"
                        num="2"
                        price="2.00"
                        :title="item.title"
                        :thumb="item.cover_img"
                         @click="goto(item.id)"

                        />
                </van-tab>
            </van-tabs>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      t_id: 0,
      list: [],
      active: 0,
      lists:[]
    };
  },
  created() {
    this.t_id = this.$route.query.id;
    // console.log(this.t_id);
    this.getnews();
    this.getlists()
  },
  methods: {
    async getnews() {
      var { data: res } = await this.$http.get(
        "http://120.53.31.103:84/api/app/teacher/" + this.t_id + "?"
      );
    //   console.log(res);
      this.list = res.data.teacher;
    //   console.log(this.list);
    },
    async getlists(){
        let {data:res} = await this.$http.post("http://120.53.31.103:84/api/app/teacher/mainCourse?teacher_id="+this.t_id )
        // console.log(res)
        this.lists=res.data.list
    },
    goto(id){
         this.$router.push({
                path:"/zhujiangx",
                query:{
                    id:id
             }
        })
    }
  }
};
</script>
<style lang="scss">
.kxiang {
  width: 100%;
  height: 100vh;
}
.kxiang-shang {
  width: 100%;
  height: 20%;
  margin-left: 20px;
  margin-top: 20px;
  .kxiang-shang-tou {
    width: 82px;
    height: 82px;
    float: left;
    // border: 1px solid white;
    // border-radius: 41px;
    img {
      width: 100%;
      height: 100%;
      border: 1px solid white;
      border-radius: 41px;
    }
  }
  .kxiang-shang-name {
    width: 200px;
    height: 28px;
    font-size: 18px;
  }
}
.kxiang-xia {
  width: 100%;
  height: 80%;
  .van-tab {
    font-size: 18px;
  }
  .kxiang-xia-yi {
    .kxiang-xia-yi-lao {
      color: #999999;
      font-size: 10px;
    }
    .kxiang-xia-yi-xiao {
      margin-top: 10px;
      font-size: 15px;
    }
  }


}
</style>