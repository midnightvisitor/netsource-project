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
                            <a @click="showSeach()">{{ setShowMsg }}<i v-bind:class="{'el-icon-arrow-down el-icon--right': styleArrow ,'el-icon-arrow-up el-icon--right': setShow}"></i></a>
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
                <a><i class="el-icon-m-arrow-down el-icon--left"></i>导入</a>
                <a @click="showExport"><i class="el-icon-upload2 el-icon--left"></i>导出</a>
            </p>
        </div>
        <div class="c-search-table">
            <el-table :data="tableData" stripe>
                <el-table-column label="序号" width="100" align="center" type="index"></el-table-column>
                <el-table-column label="设备名称" align="left" prop="value1"></el-table-column>
                <el-table-column label="所属网络" align="left" prop="value2"></el-table-column>
                <el-table-column label="所属系统" align="left" prop="value3"></el-table-column>
                <el-table-column label="设备网管标识" align="left" prop="value4"></el-table-column>
                <el-table-column label="设备厂家" align="left" prop="value5"></el-table-column>
                <el-table-column label="设备型号" align="left" prop="value6"></el-table-column>
                <el-table-column label="所属线别" align="left" prop="value7"></el-table-column>
                <el-table-column label="所属车间" align="center" prop="value8"></el-table-column>
                <el-table-column label="操作" align="center">
                    <template slot-scope="scope">
                        <div>
                            <a class="show-underline" href="#">查看</a>
                            <a class="show-underline" href="#" @click="handleShowEditDialog">编辑</a>
                            <a class="show-underline" href="#" @click="handleShowTips">删除</a>
                        </div>
                    </template>
                </el-table-column>
            </el-table>
            <!-- 分页 Start -->
            <div class="t-center mt-15">
                <el-pagination
                    background
                    layout="prev, pager, next"
                    :total="1000">
                </el-pagination>
            </div>
            <!-- 分页 End -->
        </div>
        <!-- 列表 End -->
    </div>
</template>
<script>
    export default {
        data () {
            return {
                setShow: false,
                setShowMsg: '更多查询条件',
                styleArrow: true,
                setContent: '',
                setTitle: '',
                tableData: [
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    },
                    {
                        value1: '武夷山东10G扩',
                        value2: '局干/汇聚层网络',
                        value3: '合福线SDH10G(中兴)L',
                        value4: '10-武夷山东10G扩',
                        value5: '中兴',
                        value6: 'ZXMP S385 EPE1Z20070500',
                        value7: '合福线',
                        value8: '南平北车间'
                    }
                ]
            };
        },
        methods: {
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
        }
    };
</script>
<style lang="less" scoped>
    @import "./deviceInfo.less";
</style>
