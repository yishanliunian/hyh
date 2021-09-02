<template>
    <div class="zixiang">
        <div class="zix_img">
            <img :src="att.thumb_img" alt="">
        </div>
        <h1 class="zixiang_h">{{att.title}}</h1>
        <div class="zixiang_ti">
            <p>{{att.click_rate}}次预览</p>
            <p>07-05</p>
        </div>
        <div class="zixiang_title">
             <h2 class="zixiang_h4">{{att.title}}</h2>
        </div>
       <p v-html="att.content" class="zixiang_html">

       </p>
    </div>
</template>
<script>
import  Service from "@/http/service.js"
import { addAbortSignal } from 'stream';
export default {
    data(){
        return{
            att:[]
        }
    },
    methods:{
       async getatt(){
            // /information/detail
            let res = await Service.post('/information/detail',{
                information_id: this.$route.params.id
            })
            console.log(res)
            this.att = res.data.data
        }
    },
    created(){
        this.getatt()
    }
}
</script>
<style>
.zixiang{
    width: 100%;
    height: 100%;
}
.zix_img{
    width: 100%;
    height: 350px;
    border-bottom: 1px solid #ddd;
}
.zix_img img{
    width: 100%;
    height: 100%
}
.zixiang_h{
    margin-top: 5px;
    margin-left: 10px
}
.zixiang_ti{
    display: flex;
    justify-content: space-between;
    padding-left: 20px;
    padding-right: 20px;
    margin-top: 20px;
    font-size: 10px;
}
.zixiang_title{
    width: 100%;
    text-align: center;
    margin-top: 50px;
}
.zixiang_h4{
    width: 80px;
    margin: auto;
    color: #ddd;
    font-size: 14px;
    height: 40px;
    border-bottom: 1px solid #ddd;
}
.zixiang_html{
    font-size: 18px;
    margin-top: 25px;
    margin-left: 10px;
}
</style>
