<template>
    <div class="class" >
        <van-card
            v-for="item in list" :key="item.id"
            :desc="item.introduction"
            :title="item.real_name"
            :thumb="item.avatar"
            />
    </div>
</template>

<script>
import { classs } from "@/http/api";

export default {
    data() {
        return {
            list:[]
        }
    },
    mounted(){
        this.getlist()
    },
    methods:{
       async getlist(){
           let {data:res} = await classs()
        //    console.log(res)
        this.list=res.data.list
        }
    },
}
</script>

<style lang="scss">
.class{
    width: 100%;
    height: 100vh;
    background: #e7e7e7
}
</style>
