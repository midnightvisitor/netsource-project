<!-- 用户管理编辑页面 -->
<template>
  <div class="c-main auth userEdit">
    <el-form :model="form" label-width="100px" :rules="rules" size="mini">
      <el-row>
        <el-col :span="23">
          <el-form-item label="归属机构" prop="value1">
            <el-input v-model="form.value1" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="11">
          <el-form-item label="登录账号" prop="value2">
            <el-input v-model="form.value2" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11" :offset="1">
          <el-form-item label="员工姓名" prop="value3">
            <el-input v-model="form.value3" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="11">
          <el-form-item label="手机号码">
            <el-input v-model="form.value4" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11" :offset="1">
          <el-form-item label="办公电话">
            <el-input v-model="form.value5" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="11">
          <el-form-item label="员工编号">
            <el-input v-model="form.value6" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11" :offset="1">
          <el-form-item label="电子邮箱">
            <el-input  v-model="form.value7" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="11">
          <el-form-item label="所在岗位">
            <el-input v-model="form.value8" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
        <el-col :span="11" :offset="1">
          <el-form-item label="排序号">
            <el-input v-model="form.value9" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="23">
          <el-form-item label="照片">
            <!--<el-input v-model="form.value10" auto-complete="off"></el-input>-->
          </el-form-item>
        </el-col>
      </el-row>
      <el-row>
        <el-col :span="23">
          <el-form-item label="备注">
            <el-input type="textarea" v-model="form.value11" auto-complete="off"></el-input>
          </el-form-item>
        </el-col>
      </el-row>
    </el-form>
    <div class="t-center mt-15">
      <button class="c-btn c-primary m-right-20" type="button" @click="returnList">保存</button>
      <button class="c-btn primary-color" type="button" @click="returnList">返回</button>
    </div>
  </div>
</template>
<script>
    export default {
        data () {
            return {
                form: {
                    value1: '',
                    value2: '',
                    value3: '',
                    value4: '',
                    value5: '',
                    value6: '',
                    value7: '',
                    value8: '',
                    value9: '',
                    value10: '',
                    value11: ''
                },
                rules: {
                    value1: [
                        { required: true, message: '请输入...', trigger: 'blur' },
                        { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                    ],
                    value2: [
                        { required: true, message: '请输入...', trigger: 'blur' },
                        { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                    ],
                    value3: [
                        { required: true, message: '请输入...', trigger: 'blur' },
                        { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                    ]
                }
            };
        },
        methods: {
            returnList () {
                this.$router.push({
                    path: '/deviceInfo'
                });
            }
        }
    };
</script>
<style lang="less" scoped>
    @import "./deviceInfo.less";
</style>
