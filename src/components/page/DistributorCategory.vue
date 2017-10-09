<template>
    <div class="table">
        <!-- 分销商类别设置 -->
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-menu"></i> 基础设置</el-breadcrumb-item>
                <el-breadcrumb-item>分销商类别设置</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="plugins-tips">
            <el-button icon="edit" type="primary">新 增</el-button>
        </div>
        <el-table :data="tableData" border stripe style="width: 90%">
            <el-table-column align=center prop="date" label="分销商类别">
            </el-table-column>
            <el-table-column align=center prop="name" label="加价率">
            </el-table-column>
            <el-table-column align=center prop="address" label="加价金额">
            </el-table-column>
            <el-table-column align=center label="操作">
                <template scope="scope">
                    <el-button type="success" size="small">修 改</el-button>
                    <el-button type="danger" size="small">删 除</el-button>
                </template>
            </el-table-column>
        </el-table>
        <Paginations :total="orderList.total" :max="orderList.pages"></Paginations>
        <!-- <paging :total="orderList.total" :max="orderList.pages" @changePage="changePage"></paging> -->
    </div>
</template>

<script>
import axios from 'axios';
import Datasource from 'vue-datasource';
import Paginations from './Pagination.vue';

export default {
    data: function() {
        const self = this;
        return {
            // currentPage: 1,
            // pageNo: 2,
            orderList:[
                {total:10},
                {pages:3}
            ],
            tableData: [{
                date: '2016-05-02',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1518 弄'
            }, {
                date: '2016-05-04',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1517 弄'
            }, {
                date: '2016-05-01',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1519 弄'
            }, {
                date: '2016-05-01',
                name: '王小虎',
                address: '上海市普陀区金沙江路 1519 弄'
            }]
        }
    },
    components: {
        Datasource,Paginations,
    },
    watch: {
      
    },
    ready() {
        
    },
    methods: {
       
    },
    computed: {
        
    },
    beforeMount() {
       
    }
}
</script>

<style scoped>
    body{
      font-family:"Segoe UI";
    }
    li{
      list-style:none;
    }
    a{
      text-decoration:none;
    }
    .pagination {
        position: relative;
      }
      .pagination li{
        display: inline-block;
        margin:0 5px;
      }
      .pagination li a{
        padding:.5rem 1rem;
        display:inline-block;
        border:1px solid #ddd;
        background:#fff;
        color:#0E90D2;
      }
      .pagination li a:hover{
        background:#eee;
      }
      .pagination li.active a{
        background:#0E90D2;
        color:#fff;
      }
</style>