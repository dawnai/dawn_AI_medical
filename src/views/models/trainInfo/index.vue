<template>
    <div>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm" :inline="true">
            <el-form-item label="选择模型" prop="name">
                <el-select v-model="ruleForm.name" placeholder="请选择活动区域">
                    <el-option label="GKMNet" value="GKMNet"></el-option>
                    <el-option label="LIIF" value="LIIF"></el-option>
                    <el-option label="SRGAN" value="SRGAN"></el-option>
                    <el-option label="DCGAN" value="DCGAN"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="选择显卡" prop="Ncard">
                <el-select v-model="ruleForm.Ncard" placeholder="请选择活动区域">
                    <el-option label="RTX 3090" value="5"></el-option>
                    <el-option label="RTX 4090" value="6"></el-option>
                    <el-option label="V100" value="7"></el-option>
                    <el-option label="V800" value="8"></el-option>
                    <el-option label="A800" value="9"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="选择框架" prop="demo">
                <el-select v-model="ruleForm.demo" placeholder="请选择活动区域">
                    <el-option label="Pytorch" value="11"></el-option>
                    <el-option label="TensorFlow" value="12"></el-option>
                    <el-option label="MindSpore" value="13"></el-option>
                    <el-option label="Keras" value="14"></el-option>
                    <el-option label="PaddlePaddle" value="15"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="选择CUDA" prop="cuda">
                <el-select v-model="ruleForm.cuda" placeholder="请选择活动区域">
                    <el-option label="11.1" value="16"></el-option>
                    <el-option label="10.1" value="17"></el-option>
                    <el-option label="10.2" value="18"></el-option>
                    <el-option label="9.1" value="19"></el-option>
                    <el-option label="9.2" value="20"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="选择CUDA" prop="dataSet">
                <el-select v-model="ruleForm.dataSet" placeholder="请选择活动区域">
                    <el-option label="ImageFolder" value="16"></el-option>
                    <el-option label="CustomData" value="17"></el-option>
                    <el-option label="SVHN" value="18"></el-option>
                    <el-option label="ImageFolder" value="19"></el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="计划时间" required>
                <el-col :span="11">
                    <el-form-item prop="date1">
                        <el-date-picker type="date" placeholder="选择日期" v-model="ruleForm.date1"
                            style="width: 100%;"></el-date-picker>
                    </el-form-item>
                </el-col>
                <el-col class="line" :span="2">-</el-col>
                <el-col :span="11">
                    <el-form-item prop="date2">
                        <el-time-picker placeholder="选择时间" v-model="ruleForm.date2" style="width: 100%;"></el-time-picker>
                    </el-form-item>
                </el-col>
            </el-form-item>
            <el-form-item label="可视化展示" prop="delivery">
                <el-switch v-model="ruleForm.delivery"></el-switch>
            </el-form-item>
            <el-form-item label="epoch" prop="type">
                <el-radio-group v-model="ruleForm.type">
                    <el-radio label="1000" name="type"></el-radio>
                    <el-radio label="2000" name="type"></el-radio>
                    <el-radio label="3000" name="type"></el-radio>
                    <el-radio label="4000" name="type"></el-radio>
                </el-radio-group>
            </el-form-item>
            <el-form-item label="评估标准" prop="resource">
                <el-checkbox-group v-model="ruleForm.resource">
                    <el-checkbox label="PSNR"></el-checkbox>
                    <el-checkbox label="SSIM"></el-checkbox>
                    <el-checkbox label="ACC"></el-checkbox>
                    <el-checkbox label="IoU"></el-checkbox>
                    <el-checkbox label="F1"></el-checkbox>
                </el-checkbox-group>
            </el-form-item>
            <el-form-item label="训练备注" prop="desc">
                <el-input type="textarea" v-model="ruleForm.desc"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
                <el-button @click="resetForm('ruleForm')">重置</el-button>
            </el-form-item>
        </el-form>

    </div>
</template>

<script>
export default {
    name: 'trainInfo',
    data() {
      return {
        ruleForm: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: [],
          desc: '',
          cuda:'',
          Ncard:'',
          demo:'',
          dataSet:''
        },
        rules: {
          name: [
            { required: true, message: '请选择模型', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请选择活动区域', trigger: 'change' }
          ],
          date1: [
            { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
          ],
          date2: [
            { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
          ],
          type: [
            { type: 'array', required: true, message: '请至少选择一个epoch', trigger: 'change' }
          ],
          resource: [
            { required: true, message: '请选择评估标准', trigger: 'change' }
          ],
          desc: [
            { required: true, message: '请填写训练备注', trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
}
</script>
<style></style>