<template>
  <div style="margin-top: 10px;">
    <el-tabs type="border-card">
      <el-tab-pane label="上传数据" name="first">
        <el-form ref="form" :model="form" label-width="80px">
          <el-form-item label="数据名称">
            <el-input v-model="form.name"></el-input>
          </el-form-item>
          <el-form-item label="文件类型">
            <el-select v-model="form.region" placeholder="请选择数据类型">
              <el-option label="PNG" value="shanghai"></el-option>
              <el-option label="JPEG" value="beijing"></el-option>
              <el-option label="GIF" value="beijing"></el-option>
              <el-option label="BMP" value="beijing"></el-option>
              <el-option label="TIFF" value="beijing"></el-option>
              <el-option label="SVG" value="beijing"></el-option>
              <el-option label="WebP" value="beijing"></el-option>
              <el-option label="HEIC" value="beijing"></el-option>
              <el-option label="RAW" value="beijing"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="上传时间">
            <el-col :span="11">
              <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
            </el-col>
            <el-col class="line" :span="2">-</el-col>
            <el-col :span="11">
              <el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
            </el-col>
          </el-form-item>
          <el-form-item label="可视化">
            <el-switch v-model="form.delivery"></el-switch>
          </el-form-item>
          <el-form-item label="探索内容">
            <el-checkbox-group v-model="form.type">
              <el-checkbox label="数据总量" name="type"></el-checkbox>
              <el-checkbox label="推理病理" name="type"></el-checkbox>
              <el-checkbox label="可视化病理区域" name="type"></el-checkbox>
              <el-checkbox label="标签探索" name="type"></el-checkbox>
            </el-checkbox-group>
          </el-form-item>
          <el-form-item label="结果展示">
            <el-radio-group v-model="form.resource">
              <el-radio label="表格"></el-radio>
              <el-radio label="文档"></el-radio>
            </el-radio-group>
          </el-form-item>
          <el-form-item label="数据备注">
            <el-input type="textarea" v-model="form.desc"></el-input>
          </el-form-item>

          <el-form-item label="上传数据">
            <el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/" multiple>
              <i class="el-icon-upload"></i>
              <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
              <div class="el-upload__tip" slot="tip">只能上传zip文件，且不超过500kb</div>
            </el-upload>
          </el-form-item>

          <el-form-item>
            <el-button type="primary" @click="onSubmit">立即上传</el-button>
            <el-button>取消</el-button>
          </el-form-item>
        </el-form>
      </el-tab-pane>

      <!-- 结果展示窗口 -->
      <el-tab-pane label="结果展示" name="second">
        <el-table :data="tableData" style="width: 100%" stripe>
          <el-table-column prop="date" label="上传日期" width="180">
          </el-table-column>
          <el-table-column prop="dataname" label="数据名称" width="180">
          </el-table-column>
          <el-table-column prop="name" label="所属用户" width="180">
          </el-table-column>
          <el-table-column prop="address" label="状态">
            <template slot-scope="{row}">
              <el-tag :type="row.address.type">{{ row.address.name }}</el-tag>
            </template>

          </el-table-column>
          <el-table-column prop="pprop" label="操作">
            <!-- 查看按钮 -->
            <div style="display: inline-block;margin-right: 10px;" @click="dialogVisible = true">
              <svg t="1691719175971" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                p-id="6368" width="32" height="32">
                <path
                  d="M698.71 301.02c-60.96-46.64-122.59-69.073-186.71-69.073S386.25 254.38 325.29 301.02c-60.699 46.44-120.173 116.59-177.696 210.747 57.534 94.323 117.022 164.595 177.732 211.115 60.956 46.707 122.573 69.17 186.674 69.17 64.1 0 125.718-22.463 186.674-69.17 60.71-46.52 120.198-116.792 177.732-211.115-57.523-94.157-116.997-164.307-177.696-210.747zM512 864c-161.102 0-307.306-112.03-438.613-336.088a31.959 31.959 0 0 1 0.01-32.338C204.702 271.858 350.903 160 512 160c161.097 0 307.298 111.858 438.603 335.574a31.959 31.959 0 0 1 0.01 32.338C819.306 751.971 673.102 864 512 864z m0-128c-123.712 0-224-100.288-224-224s100.288-224 224-224 224 100.288 224 224-100.288 224-224 224z"
                  fill="#5090F1" p-id="6369"></path>
                <path d="M432 432m-64 0a64 64 0 1 0 128 0 64 64 0 1 0-128 0Z" fill="#FFFFFF" p-id="6370"></path>
              </svg>
            </div>
            <!-- 删除按钮 -->
            <div style="display: inline-block;" @click="del">
              <svg t="1691719259898" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                p-id="9225" width="32" height="32">
                <path
                  d="M791.993 298.769v503.92c0 42.01-34.06 76.094-76.094 76.094h-318.74c-42.035 0-76.094-34.084-76.094-76.094v-503.92M710.217 264.958l0.63-67.646c0-42.01-8.72-76.093-50.729-76.093H460.57c-42.035 0-76.093 34.083-76.093 76.093v67.646"
                  fill="#F7E946" p-id="9226"></path>
                <path
                  d="M423.266 801.104c-14.006 0-25.364-11.344-25.364-25.365V392.944c0-14.019 11.358-25.364 25.364-25.364 14.008 0 25.365 11.345 25.365 25.364v382.794c0 14.022-11.357 25.366-25.365 25.366zM600.174 801.104c-14.008 0-25.364-11.344-25.364-25.365V392.944c0-14.019 11.356-25.364 25.364-25.364 14.007 0 25.364 11.345 25.364 25.364v382.794c0 14.022-11.357 25.366-25.364 25.366zM252.577 396.857c-14.007 0-25.365-11.344-25.365-25.364v-72.7c0-14.02 11.357-25.365 25.365-25.365s25.364 11.345 25.364 25.365v72.7c0 14.021-11.357 25.364-25.364 25.364zM252.577 546.519c-14.007 0-25.365-11.346-25.365-25.364v-79.908c0-14.021 11.357-25.366 25.365-25.366s25.364 11.345 25.364 25.366v79.908c0 14.018-11.357 25.364-25.364 25.364z"
                  fill="#213847" p-id="9227"></path>
                <path
                  d="M700.689 904.146H328.67c-55.943 0-101.458-45.502-101.458-101.458V604.826c0-14.02 11.357-25.365 25.365-25.365s25.364 11.346 25.364 25.365v197.862c0 27.966 22.751 50.729 50.729 50.729h372.019c27.979 0 50.729-22.764 50.729-50.729v-503.92c0-14.02 11.356-25.365 25.364-25.365s25.364 11.345 25.364 25.365v503.92c0.001 55.957-45.513 101.458-101.457 101.458zM710.847 290.322c-14.008 0-25.366-11.345-25.366-25.365v-67.646c0-27.965-22.75-50.729-50.729-50.729H392.081c-27.978 0-50.729 22.763-50.729 50.729v67.646c0 14.02-11.357 25.365-25.364 25.365-14.008 0-25.364-11.345-25.364-25.365v-67.646c0-55.956 45.514-101.458 101.457-101.458h242.671c55.943 0 101.458 45.502 101.458 101.458v67.646c0 14.021-11.356 25.365-25.363 25.365z"
                  fill="#213847" p-id="9228"></path>
                <path
                  d="M159.591 303.872c-13.996 0-25.353-11.345-25.365-25.34s11.32-25.364 25.339-25.389l697.522-0.842h0.025c13.994 0 25.352 11.345 25.363 25.339 0.014 13.995-11.319 25.364-25.339 25.39l-697.522 0.842h-0.023z"
                  fill="#213847" p-id="9229"></path>
              </svg>
            </div>

          </el-table-column>
        </el-table>
      </el-tab-pane>

      <el-tab-pane label="帮助文档" name="third">
        thanks
      </el-tab-pane>
      

    </el-tabs>

    <el-dialog title="预览" :visible.sync="dialogVisible" width="70%" :before-close="handleClose">
      <el-card style="margin-left: 10px;">
        <!-- 右边的标题 -->
        <div style="display: flex; justify-content: space-between;align-items: center;">
          <h1>输出/Output</h1>
          <svg t="1691637298226" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
            p-id="12886" width="50" height="50">
            <path
              d="M547.6 374.18H309.15c-18.28 0-33.1-14.81-33.1-33.1 0-18.28 14.81-33.1 33.1-33.1H547.6c18.28 0 33.1 14.81 33.1 33.1s-14.82 33.1-33.1 33.1zM639.55 618.91H305.59c-18.28 0-33.1-14.81-33.1-33.1 0-18.28 14.81-33.1 33.1-33.1h333.96c18.28 0 33.1 14.81 33.1 33.1-0.01 18.29-14.82 33.1-33.1 33.1zM874.51 869.21H618.66c-18.28 0-33.1-14.81-33.1-33.1 0-18.28 14.81-33.1 33.1-33.1h255.85c18.28 0 33.1 14.81 33.1 33.1 0 18.28-14.82 33.1-33.1 33.1z"
              fill="#4ba5d7" p-id="12887"></path>
            <path
              d="M533.31 992H136.74c-18.28 0-33.1-14.81-33.1-33.1V65.1c0-18.28 14.81-33.1 33.1-33.1H808.4c18.28 0 33.1 14.81 33.1 33.1v520.72c0 18.28-14.81 33.1-33.1 33.1s-33.1-14.81-33.1-33.1V98.19H169.84v827.62h363.48c18.28 0 33.1 14.81 33.1 33.1S551.6 992 533.31 992zM806.07 950.57a33.03 33.03 0 0 1-23.38-9.66c-12.94-12.92-12.96-33.87-0.05-46.81l57.86-57.98-57.86-57.98c-12.91-12.94-12.88-33.89 0.05-46.81s33.86-12.88 46.81 0.05l81.19 81.36c12.88 12.92 12.88 33.84 0 46.76l-81.19 81.36a33.061 33.061 0 0 1-23.43 9.71z"
              fill="#4ba5d7" p-id="12888"></path>
          </svg>
        </div>
        <!-- 下面的信息展示栏 -->
        <div>
          <el-descriptions title="数据集信息" :column="3" :size="size" border>
            <el-descriptions-item label="数据集类型"><el-tag size="small" style="margin-right: 10px;">图像</el-tag><el-tag
                size="small">png</el-tag></el-descriptions-item>
            <el-descriptions-item label="数据集大小(M)">21</el-descriptions-item>
            <el-descriptions-item label="数据量(张)">277524</el-descriptions-item>
            <el-descriptions-item label="所属用户">Admin</el-descriptions-item>
            <el-descriptions-item label="备注">
              <el-tag size="small">医疗图像</el-tag>
            </el-descriptions-item>
            <el-descriptions-item label="随机抽样个数">50</el-descriptions-item>


            <el-descriptions-item label="数据总结">
              此部分给出数据集病理情况
            </el-descriptions-item>
            <el-descriptions-item label="数据总结">
              <el-button type="primary" icon="el-icon-download">
                下载报告
              </el-button>
              <el-button type="danger" icon="el-icon-delete">
                删除报告
              </el-button>
            </el-descriptions-item>


          </el-descriptions>
        </div>


      </el-card>

      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">取 消</el-button>
        <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>


  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      },
      tableData: [{
        date: '2023-05-02',
        name: 'admin',
        dataname: 'dpdd',
        address: {
          type: 'success',
          name: '探索完成'
        },

      }, {
        date: '2023-05-04',
        name: 'dawn',
        dataname: 'img101',
        address: {
          type: 'warning',
          name: '正在解析'
        }
      }, {
        date: '2023-05-01',
        name: 'moud',
        dataname: 'uu',
        address: {
          type: 'danger',
          name: '解析失败'
        }
      }, {
        date: '2023-05-03',
        name: 'yd',
        dataname: 'yiliao',
        address: {
          type: 'success',
          name: '探索完成'
        },
      }],
      dialogVisible: false

    }
  },
  methods: {
    onSubmit() {
      console.log('submit!');
    },
    tableRowClassName({ row, rowIndex }) {
      if (rowIndex == 1) {
        return 'warning-row';
      } else if (rowIndex == 3) {
        return 'success-row';
      }
      return '';
    },
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          done();
        })
        .catch(_ => { });
    },
    del(){
      this.$message({
        type:'success',
        message:'删除成功'
      })
    }
  }
}
</script>

<style scoped>
.footer {
  display: flex;
  border-top: 1px solid #9fd2f4;
  padding-top: 10px;
  align-items: center;
}

.el-table .warning-row {
  background: red;
}

.el-table .success-row {
  background: blue;
}
</style>
