<template>
    <div style="margin-top: 10px;">
        <el-tabs tab-position="right">
            <el-tab-pane label="内置模型">
                <el-card>
                    <el-table
                        :data="tableData.filter(data => !search || data.name.toLowerCase().includes(search.toLowerCase()))"
                        style="width: 100%" stripe>
                        <el-table-column label="上传日期" prop="date">
                        </el-table-column>
                        <el-table-column label="模型名称" prop="name">
                        </el-table-column>
                        <el-table-column label="类型" prop="modelType">
                        </el-table-column>
                        <el-table-column label="任务" prop="mission">
                        </el-table-column>
                        <el-table-column label="对象" prop="modelObject">
                        </el-table-column>
                        <el-table-column label="备注" prop="modelInfo">
                        </el-table-column>
                        <el-table-column align="right">
                            <template slot="header" slot-scope="scope">
                                <el-input v-model="search" size="mini" placeholder="输入关键字搜索" />
                            </template>
                            <template slot-scope="scope">
                                <el-button size="mini" type="primary" icon="el-icon-edit">编辑</el-button>
                                <el-button size="mini" type="danger" icon="el-icon-delete">删除</el-button>
                            </template>
                        </el-table-column>
                    </el-table>
                </el-card>
            </el-tab-pane>
            <el-tab-pane label="自定义模型">
                <el-row>
                    <el-col :span="12">
                        <myLottie></myLottie>
                    </el-col>
                    <el-col :span="12">
                        <h1>上传自定义模型</h1>
                        <el-form ref="form" :model="form" label-width="80px">
                            <el-form-item label="模型名称">
                                <el-input v-model="form.name"></el-input>
                            </el-form-item>
                            <el-form-item>
                                <el-form inline>
                                    <el-form-item label="模型任务">
                                        <el-select v-model="form.region" placeholder="请选择任务">
                                            <el-option label="识别" value="shanghai"></el-option>
                                            <el-option label="检测" value="beijing"></el-option>
                                            <el-option label="分割" value="beijing"></el-option>
                                            <el-option label="归一化" value="beijing"></el-option>
                                            <el-option label="超分辨" value="beijing"></el-option>
                                            <el-option label="去模糊" value="beijing"></el-option>
                                            <el-option label="去噪" value="beijing"></el-option>
                                        </el-select>
                                    </el-form-item>
                                    <el-form-item label="类型">
                                        <el-select v-model="form.region" placeholder="请选择类型">
                                            <el-option label="CNN" value="shanghai"></el-option>
                                            <el-option label="LSTM" value="beijing"></el-option>
                                            <el-option label="RNN" value="beijing"></el-option>
                                            <el-option label="UNet" value="beijing"></el-option>
                                            <el-option label="GAN" value="beijing"></el-option>
                                            <el-option label="Transform" value="beijing"></el-option>
                                        </el-select>
                                    </el-form-item>
                                    <el-form-item label="模型框架">
                                        <el-select v-model="form.region" placeholder="请选择类型">
                                            <el-option label="Pytorch(Facebook)" value="shanghai"></el-option>
                                            <el-option label="TensorFlow(谷歌)" value="beijing"></el-option>
                                            <el-option label="Keras" value="beijing"></el-option>
                                            <el-option label="Caffe(贾扬清等)" value="beijing"></el-option>
                                            <el-option label="MXNet(亚马逊)" value="beijing"></el-option>
                                            <el-option label="Microsoft Cognitive Toolkit (CNTK)"
                                                value="beijing"></el-option>
                                            <el-option label="PaddlePaddle(百度)" value="beijing"></el-option>
                                            <el-option label="Theano" value="beijing"></el-option>
                                            <el-option label="MindSpore(华为)" value="beijing"></el-option>

                                        </el-select>
                                    </el-form-item>
                                    <el-form-item label="预训练">
                                        <el-switch v-model="form.delivery"></el-switch>
                                    </el-form-item>
                                </el-form>
                            </el-form-item>




                            <el-form-item label="模型评估">
                                <el-checkbox-group v-model="form.type">
                                    <el-checkbox label="PSNR" name="type"></el-checkbox>
                                    <el-checkbox label="ACC" name="type"></el-checkbox>
                                    <el-checkbox label="SSIM" name="type"></el-checkbox>
                                    <el-checkbox label="F1" name="type"></el-checkbox>
                                    <el-checkbox label="IoU" name="type"></el-checkbox>
                                    <el-checkbox label="Recall" name="type"></el-checkbox>
                                    <el-checkbox label="RMSE" name="type"></el-checkbox>
                                    <el-checkbox label="AP" name="type"></el-checkbox>
                                    <el-checkbox label="Pixel Accuracy" name="type"></el-checkbox>
                                    <el-checkbox label="FID" name="type"></el-checkbox>
                                </el-checkbox-group>
                            </el-form-item>

                            <el-form-item label="模型说明">
                                <el-input type="textarea" v-model="form.desc"></el-input>
                            </el-form-item>

                            <el-form-item label="class文件">
                                <el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/"
                                    multiple>
                                    <i class="el-icon-upload"></i>
                                    <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
                                    <div class="el-upload__tip" slot="tip">只能python文件</div>
                                </el-upload>
                            </el-form-item>


                            <el-form-item label="预训练文件">
                                <el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/"
                                    multiple>
                                    <i class="el-icon-upload"></i>
                                    <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
                                </el-upload>
                            </el-form-item>

                            <el-form-item>
                                <el-button type="primary">立即上传</el-button>
                                <el-button>取消</el-button>
                            </el-form-item>
                        </el-form>
                    </el-col>

                </el-row>
            </el-tab-pane>
            <el-tab-pane label="模型预训练">
                <el-row>
                    <el-col :span="12">
                        <el-card style="margin: 0px 10px;">
                            <h1>模型预训练</h1>
                            <trainInfo></trainInfo>
                        </el-card>

                    </el-col>
                    <el-col :span="12">
                        <aiTrain></aiTrain>
                    </el-col>
                </el-row>



            </el-tab-pane>
            <el-tab-pane label="模型评估">
                <el-row>
                    <el-col :span="12">
                        <el-card style="margin: 0px 5px;">
                            <h1>报告总览</h1>
                            <training></training>
                        </el-card>

                    </el-col>
                    <el-col :span="12">
                        <assess></assess>
                    </el-col>
                </el-row>
            </el-tab-pane>
        </el-tabs>
    </div>
</template>

<script>
import myLottie from './myLottie'
import aiTrain from './aiTrain'
import trainInfo from './trainInfo'
import training from './training'
import assess from './assess'
export default {
    name: 'models',
    data() {
        return {
            tableData: [{
                date: '2023-05-02',
                name: 'GKMNet',
                modelType: 'UNet',
                mission: '去模糊',
                modelObject: 'img',
                modelInfo: '1.3M'
            }, {
                date: '2023-05-12',
                name: 'LIIF',
                modelType: '迭代滤波器',
                mission: '去模糊',
                modelObject: 'img',
                modelInfo: '220M'
            }, {
                date: '2023-09-02',
                name: 'SRGAN',
                modelType: 'GAN',
                mission: '超分辨',
                modelObject: 'img',
                modelInfo: '22.3M'
            }, {
                date: '2023-09-12',
                name: 'DCGAN',
                modelType: 'GAN',
                mission: '染色标准化',
                modelObject: 'img',
                modelInfo: '13.3M'
            }],
            search: '',
            form: {
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: false,
                type: [],
                resource: '',
                desc: ''
            }
        }
    },
    components: {
        myLottie,
        aiTrain,
        trainInfo,
        training,
        assess,
    },
    methods: {

    },
}
</script>

<style></style>