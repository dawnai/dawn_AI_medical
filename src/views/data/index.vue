<template>
  <div class="contain">
    <el-tabs v-model="activeName">
      <el-tab-pane label="数据集管理" name="first">
        <el-table :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()))"
          style="width: 100%">
          <el-table-column label="时间" prop="date">
          </el-table-column>
          <el-table-column label="用户名" prop="name">
          </el-table-column>
          <el-table-column label="数据集名称" prop="dataname">
          </el-table-column>
          <el-table-column label="状态" prop="state">
            <template slot-scope="{row,index}">
              <el-tag :type="row.color">{{ row.state }}</el-tag>
            </template>

          </el-table-column>
          <el-table-column label="备注" prop="info">
          </el-table-column>

          <el-table-column align="right">
            <template slot="header" slot-scope="scope">
              <el-input v-model="search" size="mini" placeholder="输入关键字搜索" />
            </template>
            <template slot-scope="scope">
              <el-button size="mini" @click="handleEdit(scope.$index, scope.row)" icon="el-icon-edit"
                type="primary">编辑</el-button>
              <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
            </template>
          </el-table-column>
        </el-table>
      </el-tab-pane>

      <el-tab-pane label="上传数据集" name="second">
        <el-form ref="form" :model="form" label-width='120px'>
          <el-form-item label="数据集名称">
            <el-input v-model="form.name"></el-input>
            <!-- 提示文案 -->
            <el-alert title="注意：自定义的数据集中，需要提供每一个样本的路径，同时还需要提供每一个样本所对应的标签" type="info" close-text="知道了" show-icon style="margin-top: 5px;">
            </el-alert>
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
          <el-form-item label="数据增强">
            <el-switch v-model="form.delivery"></el-switch>

            <el-alert title="数据增强的效果包括排除染色操作干扰，提升模型的泛化能力" type="info" close-text="知道了" show-icon >
            </el-alert>
          </el-form-item>
          <el-form-item label="数据集备注">
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



      <el-tab-pane label="帮助文档" name="third">
        <h1>病理图像数据增强的两大方向</h1>
        <p>病理图像是搭载标本的整体载玻片扫描而得，载玻片上的组织需要经过染色后才能够放到显微镜下进行观察。最经济实惠的染色方法是H&E染色，其中H是苏木素（haematoxylin，可以将细胞核染色），E是伊红（eosin，可以将细胞液染色）。</p>
        <p>病理图像、组织图像往往呈现红色。在进行基础数据探索时便发现，<span style='font-weight: bolder;'>恶性病灶的颜色往往比良性病灶颜色更深</span> ，因此色彩的差异可能是神经网络在训练过程中需要学习的一大关键点。</p>
        <p>然而，在病理图像识别应用中总是面临的一大挑战是：<span style='font-weight: bolder;'>如何排除不同实验室、不同专业人员、不同批次染色剂、不同扫描仪器、不同玻片原材料、不同组织对颜色的响应程度等等因素而引起的颜色差异，而实现正确的识别</span></p>
        <p>病理图像的预处理/增强一般只有一种目标：<span style='font-weight: bolder;'>排除染色操作干扰，提升模型的泛化能力</span></p>
        <p>在应用时，主要从以下两个方向来提升病理模型的泛化能力</p>
        <p><span style="font-weight: bolder;color: brown;">提升样本的多样性</span>（increase diversity）：由于病理图像存在染色差异，因此模型可能需要面对色彩高度多样化的测试样本，为了能够应对这些样本应该让训练集覆盖尽量多的色彩情况，即完成色彩增强（Color Augmentation）。这是最常用的方法，只涉及到对训练集进行变化，可以帮助模型对抗过拟合</p>
        <p>具体手段包括</p>
        <p><ul>
          <li>随机仿射变换（随机移动、随机旋转、随机拉伸、随机透视等）</li>
          <li>随机噪声（高斯噪声、脉冲噪声、散粒噪声等）</li>
          <li>随机线性变换（随机亮度、随机对比度、随机色相、随机饱和度、随机色温）</li>
          <li>改变色彩空间（例如，RGB-HSV，基于反卷积的RGB-H&E，RGB-HED等）</li>
          <li>针对单通道的随机线性变换</li>
          <li>色彩均衡、自动对比度、随机翻转、随机裁剪或填充</li>
        </ul></p>
        <p><span style="font-weight: bolder;color: brown;">降低样本的多样性</span>（decrease diversity）：无论训练集、测试集上的染色有多大差异，只要将整个数据集（包括测试集和验证集）的图像进行色彩标准化（Color Normalization），让所有的图像尽可能在色彩上一致，就可以极大程度降低这种差异带来的影响。这种方法需要对训练集和测试集同时进行修改，也可以帮助模型提升泛化能力。</p>
        <p>在没有深度学习之前往往需要先寻找一个“标准图像”作为目标图像，可能是训练集/测试集中提供的某一张图像，也可能是某个实验室标准。找到目标后，再将其他图像按照目标图像进行标准化。常见的经典方法有</p>
        <p><ul>
          <li>色彩匹配（Color Matching）</li>
          <li>染色分离（stain separation）</li>
          <li>基于生成对抗网络（GANs）完成色彩标准化</li>
        </ul></p>
        <h2>
          imgaug
        </h2>
        <p>imgaug是专业用于机器学习/深度学习过程中完成图像增强的库，支持广泛的增强技术、配备有一系列管道工具供使用者轻松组合增强工具，还能够无缝与PyTorch链接使用，是第三方数据增强最常用的库之一。作为独立第三方库，imgaug有一个详尽的<a href="https://imgaug.readthedocs.io/en/latest/index.html" style="color: blue;">[官方文档]</a></p>
        <p>在imgaug当中，共有19个增强板块，包含180+具体的增强手段以及通用的类。在传统图像处理方向，例如色彩、算数等板块，imgaug包含较多功能，较为强势，在深度学习相关的领域，如卷积、池化、边缘检测等则略为弱势。</p>
        <p>在实际使用imgaug时，往往是先找到需要的增强方法，再找到imgaug中该增强方法可能存在的板块，其中<span style="font-weight: bolder;">较为常用的有</span>：</p>
        <p>
          <ul>
            <li>**通用板块**：包含增强手段排序、打包等功能</li>
            <li>**算数板块**：包含基本数学运算、各类噪声、Dropout等功能</li>
            <li>**模糊板块**：包含高斯模糊、运动模糊、偏移模糊等手段</li>
            <li>**兰德增强**：基于2021年的论文实现的兰德增强RandAugment</li>
            <li>**色彩板块**：包括改变明度、饱和度、色相、色彩空间、色温等功能</li>
            <li>**对比度板块**：包括gamma值、sigmoid对比等多个对比度</li>
            <li>**翻转板块**：包括水平翻转、垂直翻转等翻转功能</li>
            <li>**几何板块**：包括仿射变换、旋转、剪切、透视等功能</li>
            <li>**PIL板块**：包含各类PIL库常见模块，如色彩均衡、自动对比度、增强亮度</li>
            <li>**尺寸板块**：包括调节大小、各类裁剪、向外填充等功能</li>
          </ul>
        </p>
      </el-tab-pane>

      <el-tab-pane label="用户手册" name="fourth">按照指示一步一步走就行</el-tab-pane>
    </el-tabs>


  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [{
        date: '2023-05-02',
        name: '王小虎',
        dataname: 'ImageFolder',
        state: '正常',
        info: '图像数据集',
        color: 'success'
      }, {
        date: '2023-05-02',
        name: 'Dawn',
        dataname: 'CustomData',
        state: '正常',
        info: '图像数据集',
        color: 'success'
      }, {
        date: '2023-05-02',
        name: 'moud',
        dataname: 'SVHN',
        state: '禁用',
        info: '图像数据集',
        color: 'danger'
      }, {
        date: '2023-05-02',
        name: '小贾',
        dataname: 'ImageFolder',
        state: '审核中',
        info: '图像数据集',
        color: 'warning'
      }],
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
      search: '',
      activeName: 'second'
    }
  },
  methods: {
    handleEdit(index, row) {
      console.log(index, row);
    },
    handleDelete(index, row) {
      console.log(index, row);
    }
  },

}
</script>

<style scoped>
.contain {
  margin-top: 10px;
  margin-left: 10px;
}
</style>

