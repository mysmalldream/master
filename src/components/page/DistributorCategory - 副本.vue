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
            <el-table-column  align=center label="操作">
                <template scope="scope">
                    <el-button  type="success" size="small">修 改</el-button>
                    <el-button  type="danger" size="small">删 除</el-button>
                </template>
            </el-table-column>
        </el-table>
    
            <!-- <Pagination :pages="pages" :current.sync="pageNo" @navpage="msgListView"></Pagination>
            <p>当前是第<span v-text="pageNo"></span>页</p> -->
    </div>
</template>

<script>
import axios from 'axios';
import Datasource from 'vue-datasource';
// import Pagination from '../js/pagination.js';
export default {
    data: function() {
        // pageNo: 1;
        // pages:150;
        const self = this;
        return {
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
            }]
        }
    },
    components: {
        Datasource
    },
    methods: {
        changePage(values) {
            this.information.pagination.per_page = values.perpage;
            this.information.data = this.information.data;
        },
        onSearch(searchQuery) {
            this.query = searchQuery;
        },
        msgListView(curPage){
                    //根据当前页获取数据
                    this.pageNo = curPage;
                }
    },
    computed: {
        getData() {
            const self = this;
            return self.information.data.filter(function(d) {
                if (d.name.indexOf(self.query) > -1) {
                    return d;
                }
            })
        }
    },
    beforeMount() {
        if (process.env.NODE_ENV === 'development') {
            this.url = '/ms/table/source';
        };
        axios.get(this.url).then((res) => {
            this.information = res.data;
        })
    }
}
</script>

<style scoped>

</style>