<template>
   <el-row class="home" :gutter="20">
       <el-col :span="8" style="margin-top:20px">
           <el-card shadow="hover">
               <div class="user">
                   <img :src="userImg"/>
                   <div class="userinfo">
                       <p class="name">Admin</p>
                       <p class="access">超级管理员</p>
                   </div>
               </div>
               <div class="'login-info">
                   <p>上次登录时间：<span>2022-1-7</span></p>
                   <p>上次登录地点：<span>武汉</span></p>
               </div>
           </el-card>
           <el-card style="margin-top:20px;height:460px">
               <el-table :data="tableData">
                   <el-table-column
                   v-for="(val,key) in tableLabel"
                   :key="key"
                   :prop="key"
                   :label="val"
                   >
                   </el-table-column>
               </el-table>
           </el-card>

       </el-col>
       <el-col :span="16" style="margin-top:20px">
           <div class="num">
               <el-card v-for="item in countData" :key="item.name" :body-style="{display:'flex',padding:0}"> 
                   <i class="icon" :class="'el-icon-'+item.icon" :style="{background: item.color}"></i>
                   <div class="detail">
                       <p class="num">￥{{item.value}}</p>
                       <p class="txt">{{item.name}}</p>
                   </div>
               </el-card>
           </div>
           <el-card style="height:260px"></el-card>
           <div class="graph">
               <el-card style="height:260px"></el-card>
               <el-card style="height:260px"></el-card>
           </div>
       </el-col>
   </el-row>
</template>
<script>
import {getData} from '../../api/data.js'

export default{
    name:'hoMe',
    data(){
        return{
            userImg:require('../../src/assets/images/user.png'),
            tableData:[
                {
            name: 'oppo',
            todayBuy: 500,
            monthBuy: 3500,
            totalBuy: 22000
          },
          {
            name: 'vivo',
            todayBuy: 300,
            monthBuy: 2200,
            totalBuy: 24000
          },
          {
            name: '苹果',
            todayBuy: 800,
            monthBuy: 4500,
            totalBuy: 65000
          },
          {
            name: '小米',
            todayBuy: 1200,
            monthBuy: 6500,
            totalBuy: 45000
          },
          {
            name: '三星',
            todayBuy: 300,
            monthBuy: 2000,
            totalBuy: 34000
          },
          {
            name: '魅族',
            todayBuy: 350,
            monthBuy: 3000,
            totalBuy: 22000
          }
            ],
            tableLabel:{
                name:'品牌',
                todayBuy:'今日购买',
                monthBuy:'本月购买',
                totalBuy:'总购买数'
            },
            countData: [
            {
            name: "今日支付订单",
            value: 1234,
            icon: "success",
            color: "#2ec7c9",
            },
            {
            name: "今日收藏订单",
            value: 210,
            icon: "star-on",
            color: "#ffb980",
            },
            {
            name: "今日未支付订单",
            value: 1234,
            icon: "s-goods",
          color: "#5ab1ef",
        },
        {
          name: "本月支付订单",
          value: 1234,
          icon: "success",
          color: "#2ec7c9",
        },
        {
          name: "本月收藏订单",
          value: 210,
          icon: "star-on",
          color: "#ffb980",
        },
        {
          name: "本月未支付订单",
          value: 1234,
          icon: "s-goods",
          color: "#5ab1ef",
        },
      ],
      
        }
    },
    mounted() {
          getData().then(res =>{
              const {code,data} =res.data
              if(code === 20000){
                  this.tableData = data.tableData
              }
              console.log(res)
          })
      },
}
</script>
<style>
</style>