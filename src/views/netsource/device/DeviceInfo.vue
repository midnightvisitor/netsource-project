<!-- 用户管理 -->
<template>
    <div class="c-main auth userControl">
        <!-- 头部信息 Start -->
        <div class="c-search">
            <!--<button class="c-btn c-primary" @click="handleShowDialog(1)">添加操作员1</button>-->
            <table>
                <thead>
                <tr>
                    <td><nobr>设备名称</nobr></td>
                    <td><el-input size="mini"></el-input></td>
                    <td><nobr>所属线别</nobr></td>
                    <td><el-input size="mini"></el-input></td>
                    <td><nobr>所属车间</nobr></td>
                    <td><el-input size="mini"></el-input></td>
                    <td>
                        <nobr>
                            <a @click="showSeach()">
                                {{ setShowMsg }}
                                <i v-bind:class="{
                                'el-icon-arrow-down el-icon--right': styleArrow ,
                                'el-icon-arrow-up el-icon--right': setShow}"
                                ></i>
                            </a>
                            <span></span>
                            <el-button type="primary" size="small">&nbsp;查询&nbsp;</el-button>
                        </nobr>
                    </td>
                </tr>
                </thead>
                <tbody v-show="setShow">
                <tr>
                    <td><nobr>设备厂家</nobr></td>
                    <td><el-input size="mini"></el-input></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                </tr>
                </tbody>
            </table>
        </div>
        <!-- 头部信息 End -->
        <!-- 列表 Start -->
        <div class="c-title">
            <span>设备信息表</span>
            <p class="fr">
                <a @click="handleShowEditDialog"><i class="el-icon-plus el-icon--left"></i>新增</a>
                <a><i class="el-icon-download el-icon--left"></i>导入</a>
                <a @click="showExport"><i class="el-icon-upload2 el-icon--left"></i>导出</a>
            </p>
        </div>
        <div class="c-search-table">
            <!-- 分页 Start -->
            <!--<table class="c-table c-stripe c-border c-hover c-state txt-center">
                <thead class="bg-thead">
                    <tr>
                        <th>序号</th>
                        <th>设备名称</th>
                        <th>所属网络</th>
                        <th>所属系统</th>
                        <th>设备网管标识</th>
                        <th>设备厂家</th>
                        <th>设备型号</th>
                        <th>所属线别</th>
                        <th>所属车间</th>
                        <th>操作</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in list" :key="item.id"
                        :data="list.slice((currentPage-1)*pagesize,currentPage*pagesize)">
                        <td v-text="index + 1"></td>
                        <td v-text="item.name"></td>
                        <td v-text="item.net"></td>
                        <td v-text="item.system"></td>
                        <td v-text="item.title"></td>
                        <td v-text="item.vender"></td>
                        <td v-text="item.type"></td>
                        <td v-text="item.line"></td>
                        <td v-text="item.shop"></td>
                        <td>
                            <div>
                                <a class="show-underline" href="#">查看</a>
                                <a class="show-underline" href="#" @click="handleShowEditDialog">编辑</a>
                                <a class="show-underline" href="#" @click="handleShowTips">删除</a>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>-->
            <el-table :data="list.slice((currentPage-1)*pagesize,currentPage*pagesize)">
                <el-table-column type="index" label="序号"></el-table-column>
                <el-table-column prop="name" label="设备名称"></el-table-column>
                <el-table-column prop="net" label="所属网络"></el-table-column>
                <el-table-column prop="system" label="所属系统"></el-table-column>
                <el-table-column prop="title" label="设备网管标识"></el-table-column>
                <el-table-column prop="vender" label="设备厂家"></el-table-column>
                <el-table-column prop="type" label="设备型号"></el-table-column>
                <el-table-column prop="line" label="所属线别"></el-table-column>
                <el-table-column prop="shop" label="所属车间"></el-table-column>
                <el-table-column label="操作">
                    <template slot-scope="scope">
                        <div>
                            <a class="show-underline" href="#">查看</a>
                            <a class="show-underline" href="#" @click="handleShowEditDialog">编辑</a>
                            <a class="show-underline" href="#" @click="handleShowTips">删除</a>
                        </div>
                    </template>
                </el-table-column>
            </el-table>
            <div class="t-center mt-15">
                <el-pagination
                    background
                    @size-change="handleSizeChange"
                    @current-change="handleCurrentChange"
                    :current-page="currentPage"
                    :page-sizes="[5, 10, 20, 50]"
                    :page-size="pagesize"
                    layout="total, sizes, prev, pager, next, jumper"
                    prev-text="上一页"
                    next-text="下一页"
                    :total="list.length">
                </el-pagination>
            </div>
            <!-- 分页 End -->
        </div>
        <!-- 列表 End -->
    </div>
</template>
<script>
    let Mock = require('mockjs'); // 测试数据
    export default {
        data () {
            return {
                currentPage: 1,
                pagesize: 10,
                list: [],
                setShow: false,
                setShowMsg: '更多查询条件',
                styleArrow: true,
                setContent: '',
                setTitle: ''
            };
        },
        computed: {
        },
        methods: {
            getlist () {
                let data = {
                    'list|15': [
                        {
                            'id': '@guid',
                            'name': '@cword(3)',
                            'net': '@cword(3)',
                            'system': '@cword(6)',
                            'title': '@cword(5)',
                            'vender': '@city()' + '@cword(2)' + '有限公司',
                            'type': /[A-Z]{2,5}-\d{5,7}/,
                            'line': '@cword(2,3)' + '线',
                            'shop': '@cword(3,5)' + '通信车间'
                        }
                    ]
                };
                let result = Mock.mock(data);
                this.list = result.list;
            },
            handleSizeChange(size) {
                this.pagesize = size;
                console.log(`每页 ${size} 条`);
            },
            handleCurrentChange(currentPage) {
                this.currentPage = currentPage;
                console.log(`当前页: ${currentPage}`);
            },
            handleShowEditDialog () { // 编辑
                this.$router.push({
                    path: '/edit'
                });
            },
            handleShowTips () { // 删除
                this.setContent = '删除后数据将无法恢复, 是否继续?';
                this.setTitle = '删除';
                this.$confirm(this.setContent, this.setTitle, {
                    confirmButtonText: '确定',
                    cancelButtonText: '取消',
                    type: 'warning'
                }).then(() => {
                    this.$message({
                        type: 'success',
                        showClose: true,
                        message: '恭喜您，' + this.setTitle + '成功！'
                    });
                }).catch(() => {
                    this.$message({
                        type: 'info',
                        message: '已取消'
                    });
                });
            },
            showSeach () { // 更多查询条件切换
                const msg = this.setShowMsg;
                if (msg === '更多查询条件') {
                    this.setShow = true;
                    this.setShowMsg = '收起';
                } else {
                    this.setShow = false;
                    this.setShowMsg = '更多查询条件';
                }
            },
            showExport () { // 导出
                this.$router.push({
                    path: '/'
                });
            }
        },
        mounted (){
            this.getlist();
        }
    };
</script>
<style lang="less" scoped>
    @import "./deviceInfo.less";
</style>
