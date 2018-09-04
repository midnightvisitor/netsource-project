<template>
    <div class="c-main auth userControl">
        <h3>线路资源</h3>
        <el-table :data="list.slice((currpage - 1) * pagesize, currpage * pagesize)" border style="width: 100%">
            <el-table-column type="index" label="序号">
            </el-table-column>
            <el-table-column label="图片">
                <template slot-scope="scope">
                    <img :src="scope.row.image" width="40" height="40"/>
                </template>
            </el-table-column>
            <el-table-column prop="name" label="商品名称">
            </el-table-column>
            <el-table-column prop="goodsId" label="ID">
            </el-table-column>
            <el-table-column prop="price" label="价格">
            </el-table-column>
        </el-table>
        <el-pagination
            background
            layout="prev, pager, next, sizes, total, jumper"
            :page-sizes="[5, 10, 15, 20]"
            :page-size="pagesize"
            :total="list.length"
            @current-change="handleCurrentChange"
            @size-change="handleSizeChange">
        </el-pagination>
    </div>
</template>
<script>
    import axios from 'axios';
    axios.defaults.baseURL = 'https://www.easy-mock.com/mock/5ae417e4985d63275b55e177/luckLin';
    axios.defaults.timeout = 20000;
    export default {
        data () {
            return {
                msg: 8888,
                list: [],
                pagesize: 10,
                currpage: 1
            };
        },
        methods: {
            getlist () {
                let starttime = new Date();
                axios.get('/mockDrink').then(data => {
                    console.log(new Date() - starttime);
                    this.list = data.data.data;
                }).catch(err => {
                    console.error(err);
                    window.alert('请求超时，刷新重试！');
                });
            },
            handleCurrentChange (cpage) {
                this.currpage = cpage;
            },
            handleSizeChange (psize) {
                this.pagesize = psize;
            }
        },
        mounted () {
            this.getlist();
        }
    };
</script>
