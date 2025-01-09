<template>
    <div style="padding: 10px 10px;">
        <!-- 用户上传模型文件 -->
        <el-row>
            <!-- left -->
            <h1>自定义染色标准化</h1>
            <el-col :span="12">
                <h3 style="display: flex;align-items: center;justify-content:space-evenly;">Soure To Stain <svg
                        t="1692235268671" class="icon" viewBox="0 0 1083 1024" version="1.1"
                        xmlns="http://www.w3.org/2000/svg" p-id="4463" id="mx_n_1692235268674" width="32" height="32">
                        <path
                            d="M467.115865 525.097194a281.971014 281.971014 0 1 0 446.811434-344.078703 281.971014 281.971014 0 1 0-446.811434 344.078703Z"
                            fill="#E9EAEB" p-id="4464"></path>
                        <path
                            d="M652.985507 390.307246v-222.608695H252.289855v222.608695H89.043478v296.811595h905.275363v-296.811595z"
                            fill="#FFFFFF" p-id="4465"></path>
                        <path
                            d="M667.826087 345.785507h-29.681159v-163.246377H267.130435v163.246377h-29.68116v-192.927536h430.376812zM460.057971 449.669565h89.043478v29.68116h-89.043478zM1009.15942 701.95942h-59.362319v-29.681159h29.68116v-267.130435h-74.202899v-29.681159h103.884058zM608.463768 523.872464h-29.681159v-148.405797h281.971014v29.681159H608.463768z"
                            fill="#2A5082" p-id="4466"></path>
                        <path
                            d="M920.115942 449.669565h-29.681159v-133.565217c0-25.228986-19.292754-44.521739-44.52174-44.521739h-118.724637v-29.68116h118.724637c41.553623 0 74.202899 32.649275 74.202899 74.202899v133.565217z"
                            fill="#2A5082" p-id="4467"></path>
                        <path
                            d="M776.162319 326.492754l-69.750725-69.750725 69.750725-71.234783 20.776811 22.26087-48.973913 48.973913 48.973913 47.489855zM178.086957 701.95942H74.202899v-326.492753h430.376811v148.405797h-29.681159v-118.724638H103.884058v267.130435h74.202899z"
                            fill="#2A5082" p-id="4468"></path>
                        <path
                            d="M222.608696 672.278261h163.246376v29.681159H222.608696zM920.115942 954.249275H415.536232v-400.695652h504.57971v400.695652z m-474.898551-29.681159h445.217392v-341.333333H445.217391v341.333333z"
                            fill="#2A5082" p-id="4469"></path>
                        <path
                            d="M771.710145 672.278261m-44.521739 0a44.521739 44.521739 0 1 0 89.043478 0 44.521739 44.521739 0 1 0-89.043478 0Z"
                            fill="#A3D4FF" p-id="4470"></path>
                        <path
                            d="M771.710145 731.64058c-32.649275 0-59.362319-26.713043-59.362319-59.362319s26.713043-59.362319 59.362319-59.362319 59.362319 26.713043 59.362319 59.362319-26.713043 59.362319-59.362319 59.362319z m0-89.043479c-16.324638 0-29.681159 13.356522-29.681159 29.68116s13.356522 29.681159 29.681159 29.681159 29.681159-13.356522 29.681159-29.681159-13.356522-29.681159-29.681159-29.68116z"
                            fill="#2A5082" p-id="4471"></path>
                        <path
                            d="M756.869565 776.162319l-51.942029 51.942029-111.304348-111.304348-163.246376 163.246377v59.362319h474.89855v-29.68116z"
                            fill="#A3D4FF" p-id="4472"></path>
                        <path
                            d="M920.115942 954.249275H415.536232v-80.13913l178.086956-178.086957 111.304348 111.304348 51.942029-51.942029 163.246377 146.921739v51.942029z m-474.898551-29.681159h445.217392v-8.904348l-133.565218-120.208696-31.165217 31.165218 41.553623 41.553623-20.776812 22.26087L593.623188 737.576812l-148.405797 148.405797v38.585507zM890.434783 479.350725h29.681159v29.681159h-29.681159zM356.173913 850.365217h-118.724638c-41.553623 0-74.202899-32.649275-74.202898-74.202898v-148.405797h29.681159v148.405797c0 25.228986 19.292754 44.521739 44.521739 44.521739h118.724638v29.681159z"
                            fill="#2A5082" p-id="4473"></path>
                        <path
                            d="M307.2 905.275362l-20.776812-22.260869 48.973913-47.489855-48.973913-48.973913 20.776812-22.26087 69.750725 71.234783zM163.246377 568.394203h29.681159v29.681159h-29.681159zM163.246377 509.031884h29.681159v29.681159h-29.681159zM163.246377 449.669565h29.681159v29.68116h-29.681159z"
                            fill="#2A5082" p-id="4474"></path>
                    </svg></h3>
                <el-card style="margin-right: 5px;">
                    <el-form ref="form" :model="form" label-width="100px">
                        <el-form-item label="名称">
                            <el-input v-model="form.name"></el-input>
                        </el-form-item>
                        <el-form-item label="目标染色剂">
                            <el-select v-model="form.region" placeholder="请选择转换后的目标染色剂">
                                <el-option label="甲基蓝" value="shanghai"></el-option>
                                <el-option label="伊红" value="beijing"></el-option>
                                <el-option label="茚菁紫" value="beijing"></el-option>
                                <el-option label="伊红和血红木素染色" value="beijing"></el-option>
                                <el-option label="二氮嗪基联苯胺" value="beijing"></el-option>
                                <el-option label="碱性磷酸酶染色" value="beijing"></el-option>
                                <el-option label="乙溴化丙啶" value="beijing"></el-option>
                                <el-option label="吖啶橙" value="beijing"></el-option>
                                <el-option label="酒红" value="beijing"></el-option>
                                <el-option label="亮蓝FCF" value="beijing"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item label="模型选择">
                            <el-select v-model="form.region" placeholder="请选择合适的模型">
                                <el-option label="CGAN" value="shanghai"></el-option>
                                <el-option label="DCGAN" value="beijing"></el-option>
                                <el-option label="STST" value="beijing"></el-option>
                                <el-option label="Vahadane" value="beijing"></el-option>
                            </el-select>
                            <!-- 提示文字 -->
                            <el-alert title="没有想要的模型？点击上传" type="info" show-icon
                                style="display: flex; height: 30px;margin-top: 5px;">

                            </el-alert>
                        </el-form-item>
                        <el-form-item label="下载报告">
                            <el-switch v-model="form.delivery"></el-switch>
                        </el-form-item>
                        <el-form-item label="评估标准">
                            <el-checkbox-group v-model="form.type">
                                <el-checkbox label="PSNR" name="type"></el-checkbox>
                                <el-checkbox label="SSIM" name="type"></el-checkbox>
                                <el-checkbox label="ACC" name="type"></el-checkbox>
                                <el-checkbox label="F1" name="type"></el-checkbox>
                                <el-checkbox label="ROC和AUC" name="type"></el-checkbox>
                                <el-checkbox label="IoU" name="type"></el-checkbox>
                                <el-checkbox label="FID" name="type"></el-checkbox>
                            </el-checkbox-group>
                        </el-form-item>
                        <el-form-item label="上传数据">
                            <el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/"
                                multiple>
                                <i class="el-icon-upload"></i>
                                <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
                                <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div>
                            </el-upload>
                        </el-form-item>
                        <el-form-item label="数据备注">
                            <el-input type="textarea" v-model="form.desc"></el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary">立即创建</el-button>
                            <el-button>取消</el-button>
                        </el-form-item>
                    </el-form>
                </el-card>
            </el-col>
            <!-- right -->
            <el-col :span="12">
                <h3 style="display: flex;align-items: center;justify-content:space-evenly;">Stain To Stain <svg
                        t="1692235760666" class="icon" viewBox="0 0 1459 1024" version="1.1"
                        xmlns="http://www.w3.org/2000/svg" p-id="8412" width="32" height="32">
                        <path
                            d="M1147.5456 787.6352l131.072 74.8544 34.8672-60.4672-131.584-75.1616 4.7872-253.8752L934.4 323.84l-220.672 125.3632-185.088-109.44 6.272-169.728-69.1712-1.6128-6.2208 167.6032-225.8432 128.3072-4.8128 256.1536-143.232 82.432 33.792 60.16 143.4624-82.5856 217.4464 128.5632 220.6464-125.3376 222.2592 131.2768 224.256-127.36zM481.8688 828.928l-183.808-108.672 4.0704-215.424 187.9552-106.8032 183.8592 108.672-4.1216 215.424-187.9552 106.8032z m259.072-102.7328l4.096-215.3984 187.904-106.752 183.8592 108.6464-4.096 215.424-187.9552 106.752-183.808-108.672z"
                            fill="#4ba5d7" p-id="8413"></path>
                        <path
                            d="M351.7696 540.672l34.6112 0.0512-2.6112 176.896-34.5856-0.0512 2.5856-176.896z m449.28 134.5536l-18.0224 29.9008 150.6304 89.7792 18.0224-29.9008-150.6304-89.7792z"
                            fill="#4ba5d7" p-id="8414"></path>
                        <path
                            d="M1313.1264 316.5696c-0.3328 0.384-1.152-0.2816-2.3552-1.3312L1147.904 178.0736c-1.2288-1.024-2.048-2.0736-1.6896-2.1248l29.44-37.7856c0.3072-0.384 1.1264 0.2816 2.3552 1.3312l163.2 137.1392c1.2288 1.024 2.048 2.0736 1.6896 2.1248l-29.7984 37.8112z m58.2144-172.0576l-75.0848-64.9472c-18.944-16.4096-43.7248-18.0992-61.3376-6.1696-3.5072 2.6112-6.9632 5.632-9.6256 9.2928l-18.0736 23.5008c-1.3568 1.664-2.304 3.6608-3.6608 5.3248 0.4096 0.3328 0.4352 0.7168 0.8448 1.0752l155.3408 134.0416 0.8192 0.6912a45.056 45.056 0 0 0 4.0704-4.5824l18.0736-23.5008c2.6624-3.6864 4.9408-7.7312 6.4-12.0832 8.2688-20.736 1.152-46.6176-17.7664-62.6432z m-290.56 479.5648c-0.4608 3.5072 214.3232-274.176 214.3232-274.176 1.3312-2.048 2.7136-3.6864 2.304-4.0448l-34.8416-29.5936c-0.4096-0.3584-1.792 1.28-3.1232 3.328l-210.688 272.3328-4.992 3.8912s-88.192 37.2992-90.4448 37.504c-1.8944 0.1536-12.6464-10.0352-12.6464-10.0352s-10.1376-7.552-10.3168-9.472c-0.1536-1.8944 17.9712-106.8288 17.9712-106.8288L1157.9136 234.752c1.3312-2.048 2.7136-3.6864 2.304-4.0448l-32.4096-27.4944c-0.4096-0.3584-1.792 1.28-3.0976 3.328l-213.4528 275.6608c-0.3328 0.4096-3.072 3.712-3.328 5.2736l-31.8208 182.9376a24.704 24.704 0 0 0-2.2528 13.2608c1.536 13.312 12.6208 22.7072 25.4208 21.5808a24.6528 24.6528 0 0 0 11.3664-4.4544 4.0704 4.0704 0 0 0 1.8432-0.512s157.7216-66.816 160.1536-69.3504l8.1408-6.8608z m146.8416-332.8512l-42.752-36.1216c-0.4096-0.3584-1.792 0.896-3.0976 2.9184L974.5152 526.848a13.7216 13.7216 0 0 0-2.304 3.6352l32.4864 3.9936c1.536 0.6144 3.1232 1.6384 3.6608 3.4816l0.0512 0.768 7.3216 28.2112a16.3328 16.3328 0 0 0 2.7392-2.8928L1225.728 295.168c0.9472-1.9712 1.92-3.584 1.8944-3.968z"
                            fill="#4ba5d7" p-id="8415"></path>
                    </svg></h3>
                <el-card  style="margin-left: 5px;">
                    <el-form ref="form" :model="form" label-width="100px">
                        <el-form-item label="名称">
                            <el-input v-model="form.name"></el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-form :inline="true">
                                <el-form-item label="源图像染色剂">
                                    <el-select v-model="form.region" placeholder="请选择转换后的目标染色剂">
                                        <el-option label="甲基蓝" value="shanghai"></el-option>
                                        <el-option label="伊红" value="beijing"></el-option>
                                        <el-option label="茚菁紫" value="beijing"></el-option>
                                        <el-option label="伊红和血红木素染色" value="beijing"></el-option>
                                        <el-option label="二氮嗪基联苯胺" value="beijing"></el-option>
                                        <el-option label="碱性磷酸酶染色" value="beijing"></el-option>
                                        <el-option label="乙溴化丙啶" value="beijing"></el-option>
                                        <el-option label="吖啶橙" value="beijing"></el-option>
                                        <el-option label="酒红" value="beijing"></el-option>
                                        <el-option label="亮蓝FCF" value="beijing"></el-option>
                                    </el-select>
                                </el-form-item>
                                <el-form-item label="目标染色剂">
                                    <el-select v-model="form.region" placeholder="请选择转换后的目标染色剂">
                                        <el-option label="甲基蓝" value="shanghai"></el-option>
                                        <el-option label="伊红" value="beijing"></el-option>
                                        <el-option label="茚菁紫" value="beijing"></el-option>
                                        <el-option label="伊红和血红木素染色" value="beijing"></el-option>
                                        <el-option label="二氮嗪基联苯胺" value="beijing"></el-option>
                                        <el-option label="碱性磷酸酶染色" value="beijing"></el-option>
                                        <el-option label="乙溴化丙啶" value="beijing"></el-option>
                                        <el-option label="吖啶橙" value="beijing"></el-option>
                                        <el-option label="酒红" value="beijing"></el-option>
                                        <el-option label="亮蓝FCF" value="beijing"></el-option>
                                    </el-select>
                                </el-form-item>
                            </el-form>

                        </el-form-item>


                        <el-form-item label="模型选择">
                            <el-select v-model="form.region" placeholder="请选择合适的模型">
                                <el-option label="CGAN" value="shanghai"></el-option>
                                <el-option label="DCGAN" value="beijing"></el-option>
                                <el-option label="STST" value="beijing"></el-option>
                                <el-option label="Vahadane" value="beijing"></el-option>
                            </el-select>
                            <!-- 提示文字 -->
                            <el-alert title="没有想要的模型？点击上传" type="info" show-icon
                                style="display: flex; height: 30px;margin-top: 5px;">

                            </el-alert>
                        </el-form-item>
                        <el-form-item label="下载报告">
                            <el-switch v-model="form.delivery"></el-switch>
                        </el-form-item>
                        <el-form-item label="评估标准">
                            <el-checkbox-group v-model="form.type">
                                <el-checkbox label="PSNR" name="type"></el-checkbox>
                                <el-checkbox label="SSIM" name="type"></el-checkbox>
                                <el-checkbox label="ACC" name="type"></el-checkbox>
                                <el-checkbox label="F1" name="type"></el-checkbox>
                                <el-checkbox label="ROC和AUC" name="type"></el-checkbox>
                                <el-checkbox label="IoU" name="type"></el-checkbox>
                                <el-checkbox label="FID" name="type"></el-checkbox>
                            </el-checkbox-group>
                        </el-form-item>
                        <el-form-item label="上传数据">
                            <el-upload class="upload-demo" drag action="https://jsonplaceholder.typicode.com/posts/"
                                multiple>
                                <i class="el-icon-upload"></i>
                                <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
                                <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div>
                            </el-upload>
                        </el-form-item>
                        <el-form-item label="数据备注">
                            <el-input type="textarea" v-model="form.desc"></el-input>
                        </el-form-item>
                        <el-form-item>
                            <el-button type="primary">立即创建</el-button>
                            <el-button>取消</el-button>
                        </el-form-item>
                    </el-form>
                </el-card>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="12">
                <el-card style="margin-right: 5px;">
                    <div style="height: 400px;width: 100%;" ref="line"></div>
                </el-card>
            </el-col>
            <el-col :span="12">
                <el-card style="margin-left: 5px;">
                    <div style="height: 400px;width: 100%;" ref="dot"></div>
                </el-card>
            </el-col>
        </el-row>
        <el-row>
            <h1>DCGAN网络</h1>
            <el-col :span="6" style="padding: 0px 5px;">
                <el-card>
                    <div style="width: 100%; height: 400px;" ref="lineGan">
                    </div>
                </el-card>

            </el-col>
            <el-col :span="6" style="padding: 0px 5px;">
                <el-card>
                    <div style="width: 100%; height: 400px;" ref="linePSNR">
                    </div>
                </el-card>

            </el-col>
            <el-col :span="6" style="padding: 0px 5px;">
                <el-card>
                    <div style="width: 100%; height: 400px;" ref="barGAN">
                    </div>
                </el-card>

            </el-col>
            <el-col :span="6" style="padding: 0px 5px;">
                <el-card>
                    <div style="width: 100%; height: 400px;" ref="linebarGAN">
                    </div>
                </el-card>
            </el-col>
        </el-row>

    </div>
</template>

<script>
import echarts from 'echarts'
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
            }
        }
    },
    mounted() {
        let myChart = echarts.init(this.$refs.line)
        myChart.setOption({
            color: ['#80FFA5', '#00DDFF', '#37A2FF', '#FF0087', '#FFBF00'],
            title: {
                text: '主流网络染色剂的使用对比'
            },
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'cross',
                    label: {
                        backgroundColor: '#6a7985'
                    }
                }
            },
            legend: {
                data: ['甲基红', '卡伦斯荧光素', '丙烯蓝', '细胞质酯酶', '草酰']
            },
            toolbox: {
                feature: {
                    saveAsImage: {}
                }
            },
            grid: {
                left: '3%',
                right: '4%',
                bottom: '3%',
                containLabel: true
            },
            xAxis: [
                {
                    type: 'category',
                    boundaryGap: false,
                    data: ['cGAN', 'Transform', 'ResNet', 'LSTM', 'CNN', 'RNN', 'U-Net']
                }
            ],
            yAxis: [
                {
                    type: 'value'
                }
            ],
            series: [
                {
                    name: '甲基红',
                    type: 'line',
                    stack: 'Total',
                    smooth: true,
                    lineStyle: {
                        width: 0
                    },
                    showSymbol: false,
                    areaStyle: {
                        opacity: 0.8,
                        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            {
                                offset: 0,
                                color: 'rgb(128, 255, 165)'
                            },
                            {
                                offset: 1,
                                color: 'rgb(1, 191, 236)'
                            }
                        ])
                    },
                    emphasis: {
                        focus: 'series'
                    },
                    data: [140, 232, 101, 264, 90, 340, 250]
                },
                {
                    name: '卡伦斯荧光素',
                    type: 'line',
                    stack: 'Total',
                    smooth: true,
                    lineStyle: {
                        width: 0
                    },
                    showSymbol: false,
                    areaStyle: {
                        opacity: 0.8,
                        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            {
                                offset: 0,
                                color: 'rgb(0, 221, 255)'
                            },
                            {
                                offset: 1,
                                color: 'rgb(77, 119, 255)'
                            }
                        ])
                    },
                    emphasis: {
                        focus: 'series'
                    },
                    data: [120, 282, 111, 234, 220, 340, 310]
                },
                {
                    name: '丙烯蓝',
                    type: 'line',
                    stack: 'Total',
                    smooth: true,
                    lineStyle: {
                        width: 0
                    },
                    showSymbol: false,
                    areaStyle: {
                        opacity: 0.8,
                        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            {
                                offset: 0,
                                color: 'rgb(55, 162, 255)'
                            },
                            {
                                offset: 1,
                                color: 'rgb(116, 21, 219)'
                            }
                        ])
                    },
                    emphasis: {
                        focus: 'series'
                    },
                    data: [320, 132, 201, 334, 190, 130, 220]
                },
                {
                    name: '细胞质酯酶',
                    type: 'line',
                    stack: 'Total',
                    smooth: true,
                    lineStyle: {
                        width: 0
                    },
                    showSymbol: false,
                    areaStyle: {
                        opacity: 0.8,
                        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            {
                                offset: 0,
                                color: 'rgb(255, 0, 135)'
                            },
                            {
                                offset: 1,
                                color: 'rgb(135, 0, 157)'
                            }
                        ])
                    },
                    emphasis: {
                        focus: 'series'
                    },
                    data: [220, 402, 231, 134, 190, 230, 120]
                },
                {
                    name: '草酰',
                    type: 'line',
                    stack: 'Total',
                    smooth: true,
                    lineStyle: {
                        width: 0
                    },
                    showSymbol: false,
                    label: {
                        show: true,
                        position: 'top'
                    },
                    areaStyle: {
                        opacity: 0.8,
                        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                            {
                                offset: 0,
                                color: 'rgb(255, 191, 0)'
                            },
                            {
                                offset: 1,
                                color: 'rgb(224, 62, 76)'
                            }
                        ])
                    },
                    emphasis: {
                        focus: 'series'
                    },
                    data: [220, 302, 181, 234, 210, 290, 150]
                }
            ]
        })
        let myDot = echarts.init(this.$refs.dot)
        myDot.setOption({
            title: {
                text: '模型大小和使用量的关系',
                subtext: 'Data from:  2003'
            },
            grid: {
                left: '3%',
                right: '7%',
                bottom: '7%',
                containLabel: true
            },
            tooltip: {
                // trigger: 'axis',
                showDelay: 0,
                formatter: function (params) {
                    if (params.value.length > 1) {
                        return (
                            params.seriesName +
                            ' :<br/>' +
                            params.value[0] +
                            'cm ' +
                            params.value[1] +
                            'kg '
                        );
                    } else {
                        return (
                            params.seriesName +
                            ' :<br/>' +
                            params.name +
                            ' : ' +
                            params.value +
                            'kg '
                        );
                    }
                },
                axisPointer: {
                    show: true,
                    type: 'cross',
                    lineStyle: {
                        type: 'dashed',
                        width: 1
                    }
                }
            },
            toolbox: {
                feature: {
                    dataZoom: {},
                    brush: {
                        type: ['rect', 'polygon', 'clear']
                    }
                }
            },
            brush: {},
            legend: {
                data: ['CNN', 'Transform'],
                left: 'center',
                bottom: 10
            },
            xAxis: [
                {
                    type: 'value',
                    scale: true,
                    axisLabel: {
                        formatter: '{value} MB'
                    },
                    splitLine: {
                        show: false
                    }
                }
            ],
            yAxis: [
                {
                    type: 'value',
                    scale: true,
                    axisLabel: {
                        formatter: '{value} '
                    },
                    splitLine: {
                        show: false
                    }
                }
            ],
            series: [
                {
                    name: 'CNN',
                    type: 'scatter',
                    emphasis: {
                        focus: 'series'
                    },
                    // prettier-ignore
                    data: [[161.2, 51.6], [167.5, 59.0], [159.5, 49.2], [157.0, 63.0], [155.8, 53.6],
                    [170.0, 59.0], [159.1, 47.6], [166.0, 69.8], [176.2, 66.8], [160.2, 75.2],
                    [172.5, 55.2], [170.9, 54.2], [172.9, 62.5], [153.4, 42.0], [160.0, 50.0],
                    [147.2, 49.8], [168.2, 49.2], [175.0, 73.2], [157.0, 47.8], [167.6, 68.8],
                    [159.5, 50.6], [175.0, 82.5], [166.8, 57.2], [176.5, 87.8], [170.2, 72.8],
                    [174.0, 54.5], [173.0, 59.8], [179.9, 67.3], [170.5, 67.8], [160.0, 47.0],
                    [154.4, 46.2], [162.0, 55.0], [176.5, 83.0], [160.0, 54.4], [152.0, 45.8],
                    [162.1, 53.6], [170.0, 73.2], [160.2, 52.1], [161.3, 67.9], [166.4, 56.6],
                    [168.9, 62.3], [163.8, 58.5], [167.6, 54.5], [160.0, 50.2], [161.3, 60.3],
                    [167.6, 58.3], [165.1, 56.2], [160.0, 50.2], [170.0, 72.9], [157.5, 59.8],
                    [167.6, 61.0], [160.7, 69.1], [163.2, 55.9], [152.4, 46.5], [157.5, 54.3],
                    [168.3, 54.8], [180.3, 60.7], [165.5, 60.0], [165.0, 62.0], [164.5, 60.3],
                    [156.0, 52.7], [160.0, 74.3], [163.0, 62.0], [165.7, 73.1], [161.0, 80.0],
                    [162.0, 54.7], [166.0, 53.2], [174.0, 75.7], [172.7, 61.1], [167.6, 55.7],
                    [151.1, 48.7], [164.5, 52.3], [163.5, 50.0], [152.0, 59.3], [169.0, 62.5],
                    [164.0, 55.7], [161.2, 54.8], [155.0, 45.9], [170.0, 70.6], [176.2, 67.2],
                    [170.0, 69.4], [162.5, 58.2], [170.3, 64.8], [164.1, 71.6], [169.5, 52.8],
                    [163.2, 59.8], [154.5, 49.0], [159.8, 50.0], [173.2, 69.2], [170.0, 55.9],
                    [161.4, 63.4], [169.0, 58.2], [166.2, 58.6], [159.4, 45.7], [162.5, 52.2],
                    [159.0, 48.6], [162.8, 57.8], [159.0, 55.6], [179.8, 66.8], [162.9, 59.4],
                    [161.0, 53.6], [151.1, 73.2], [168.2, 53.4], [168.9, 69.0], [173.2, 58.4],
                    [171.8, 56.2], [178.0, 70.6], [164.3, 59.8], [163.0, 72.0], [168.5, 65.2],
                    [166.8, 56.6], [172.7, 105.2], [163.5, 51.8], [169.4, 63.4], [167.8, 59.0],
                    [159.5, 47.6], [167.6, 63.0], [161.2, 55.2], [160.0, 45.0], [163.2, 54.0],
                    [162.2, 50.2], [161.3, 60.2], [149.5, 44.8], [157.5, 58.8], [163.2, 56.4],
                    [172.7, 62.0], [155.0, 49.2], [156.5, 67.2], [164.0, 53.8], [160.9, 54.4],
                    [162.8, 58.0], [167.0, 59.8], [160.0, 54.8], [160.0, 43.2], [168.9, 60.5],
                    [158.2, 46.4], [156.0, 64.4], [160.0, 48.8], [167.1, 62.2], [158.0, 55.5],
                    [167.6, 57.8], [156.0, 54.6], [162.1, 59.2], [173.4, 52.7], [159.8, 53.2],
                    [170.5, 64.5], [159.2, 51.8], [157.5, 56.0], [161.3, 63.6], [162.6, 63.2],
                    [160.0, 59.5], [168.9, 56.8], [165.1, 64.1], [162.6, 50.0], [165.1, 72.3],
                    [166.4, 55.0], [160.0, 55.9], [152.4, 60.4], [170.2, 69.1], [162.6, 84.5],
                    [170.2, 55.9], [158.8, 55.5], [172.7, 69.5], [167.6, 76.4], [162.6, 61.4],
                    [167.6, 65.9], [156.2, 58.6], [175.2, 66.8], [172.1, 56.6], [162.6, 58.6],
                    [160.0, 55.9], [165.1, 59.1], [182.9, 81.8], [166.4, 70.7], [165.1, 56.8],
                    [177.8, 60.0], [165.1, 58.2], [175.3, 72.7], [154.9, 54.1], [158.8, 49.1],
                    [172.7, 75.9], [168.9, 55.0], [161.3, 57.3], [167.6, 55.0], [165.1, 65.5],
                    [175.3, 65.5], [157.5, 48.6], [163.8, 58.6], [167.6, 63.6], [165.1, 55.2],
                    [165.1, 62.7], [168.9, 56.6], [162.6, 53.9], [164.5, 63.2], [176.5, 73.6],
                    [168.9, 62.0], [175.3, 63.6], [159.4, 53.2], [160.0, 53.4], [170.2, 55.0],
                    [162.6, 70.5], [167.6, 54.5], [162.6, 54.5], [160.7, 55.9], [160.0, 59.0],
                    [157.5, 63.6], [162.6, 54.5], [152.4, 47.3], [170.2, 67.7], [165.1, 80.9],
                    [172.7, 70.5], [165.1, 60.9], [170.2, 63.6], [170.2, 54.5], [170.2, 59.1],
                    [161.3, 70.5], [167.6, 52.7], [167.6, 62.7], [165.1, 86.3], [162.6, 66.4],
                    [152.4, 67.3], [168.9, 63.0], [170.2, 73.6], [175.2, 62.3], [175.2, 57.7],
                    [160.0, 55.4], [165.1, 104.1], [174.0, 55.5], [170.2, 77.3], [160.0, 80.5],
                    [167.6, 64.5], [167.6, 72.3], [167.6, 61.4], [154.9, 58.2], [162.6, 81.8],
                    [175.3, 63.6], [171.4, 53.4], [157.5, 54.5], [165.1, 53.6], [160.0, 60.0],
                    [174.0, 73.6], [162.6, 61.4], [174.0, 55.5], [162.6, 63.6], [161.3, 60.9],
                    [156.2, 60.0], [149.9, 46.8], [169.5, 57.3], [160.0, 64.1], [175.3, 63.6],
                    [169.5, 67.3], [160.0, 75.5], [172.7, 68.2], [162.6, 61.4], [157.5, 76.8],
                    [176.5, 71.8], [164.4, 55.5], [160.7, 48.6], [174.0, 66.4], [163.8, 67.3]
                    ],
                    markArea: {
                        silent: true,
                        itemStyle: {
                            color: 'transparent',
                            borderWidth: 1,
                            borderType: 'dashed'
                        },
                        data: [
                            [
                                {
                                    name: 'CNN NetWork',
                                    xAxis: 'min',
                                    yAxis: 'min'
                                },
                                {
                                    xAxis: 'max',
                                    yAxis: 'max'
                                }
                            ]
                        ]
                    },
                    markPoint: {
                        data: [
                            { type: 'max', name: 'Max' },
                            { type: 'min', name: 'Min' }
                        ]
                    },
                    markLine: {
                        lineStyle: {
                            type: 'solid'
                        },
                        data: [{ type: 'average', name: 'AVG' }, { xAxis: 160 }]
                    }
                },
                {
                    name: 'Transform',
                    type: 'scatter',
                    emphasis: {
                        focus: 'series'
                    },
                    // prettier-ignore
                    data: [[174.0, 65.6], [175.3, 71.8], [193.5, 80.7], [186.5, 72.6], [187.2, 78.8],
                    [181.5, 74.8], [184.0, 86.4], [184.5, 78.4], [175.0, 62.0], [184.0, 81.6],
                    [180.0, 76.6], [177.8, 83.6], [192.0, 90.0], [176.0, 74.6], [174.0, 71.0],
                    [184.0, 79.6], [192.7, 93.8], [171.5, 70.0], [173.0, 72.4], [176.0, 85.9],
                    [176.0, 78.8], [180.5, 77.8], [172.7, 66.2], [176.0, 86.4], [173.5, 81.8],
                    [178.0, 89.6], [180.3, 82.8], [180.3, 76.4], [164.5, 63.2], [173.0, 60.9],
                    [183.5, 74.8], [175.5, 70.0], [188.0, 72.4], [189.2, 84.1], [172.8, 69.1],
                    [170.0, 59.5], [182.0, 67.2], [170.0, 61.3], [177.8, 68.6], [184.2, 80.1],
                    [186.7, 87.8], [171.4, 84.7], [172.7, 73.4], [175.3, 72.1], [180.3, 82.6],
                    [182.9, 88.7], [188.0, 84.1], [177.2, 94.1], [172.1, 74.9], [167.0, 59.1],
                    [169.5, 75.6], [174.0, 86.2], [172.7, 75.3], [182.2, 87.1], [164.1, 55.2],
                    [163.0, 57.0], [171.5, 61.4], [184.2, 76.8], [174.0, 86.8], [174.0, 72.2],
                    [177.0, 71.6], [186.0, 84.8], [167.0, 68.2], [171.8, 66.1], [182.0, 72.0],
                    [167.0, 64.6], [177.8, 74.8], [164.5, 70.0], [192.0, 101.6], [175.5, 63.2],
                    [171.2, 79.1], [181.6, 78.9], [167.4, 67.7], [181.1, 66.0], [177.0, 68.2],
                    [174.5, 63.9], [177.5, 72.0], [170.5, 56.8], [182.4, 74.5], [197.1, 90.9],
                    [180.1, 93.0], [175.5, 80.9], [180.6, 72.7], [184.4, 68.0], [175.5, 70.9],
                    [180.6, 72.5], [177.0, 72.5], [177.1, 83.4], [181.6, 75.5], [176.5, 73.0],
                    [175.0, 70.2], [174.0, 73.4], [165.1, 70.5], [177.0, 68.9], [192.0, 102.3],
                    [176.5, 68.4], [169.4, 65.9], [182.1, 75.7], [179.8, 84.5], [175.3, 87.7],
                    [184.9, 86.4], [177.3, 73.2], [167.4, 53.9], [178.1, 72.0], [168.9, 55.5],
                    [157.2, 58.4], [180.3, 83.2], [170.2, 72.7], [177.8, 64.1], [172.7, 72.3],
                    [165.1, 65.0], [186.7, 86.4], [165.1, 65.0], [174.0, 88.6], [175.3, 84.1],
                    [185.4, 66.8], [177.8, 75.5], [180.3, 93.2], [180.3, 82.7], [177.8, 58.0],
                    [177.8, 79.5], [177.8, 78.6], [177.8, 71.8], [177.8, 116.4], [163.8, 72.2],
                    [188.0, 83.6], [198.1, 85.5], [175.3, 90.9], [166.4, 85.9], [190.5, 89.1],
                    [166.4, 75.0], [177.8, 77.7], [179.7, 86.4], [172.7, 90.9], [190.5, 73.6],
                    [185.4, 76.4], [168.9, 69.1], [167.6, 84.5], [175.3, 64.5], [170.2, 69.1],
                    [190.5, 108.6], [177.8, 86.4], [190.5, 80.9], [177.8, 87.7], [184.2, 94.5],
                    [176.5, 80.2], [177.8, 72.0], [180.3, 71.4], [171.4, 72.7], [172.7, 84.1],
                    [172.7, 76.8], [177.8, 63.6], [177.8, 80.9], [182.9, 80.9], [170.2, 85.5],
                    [167.6, 68.6], [175.3, 67.7], [165.1, 66.4], [185.4, 102.3], [181.6, 70.5],
                    [172.7, 95.9], [190.5, 84.1], [179.1, 87.3], [175.3, 71.8], [170.2, 65.9],
                    [193.0, 95.9], [171.4, 91.4], [177.8, 81.8], [177.8, 96.8], [167.6, 69.1],
                    [167.6, 82.7], [180.3, 75.5], [182.9, 79.5], [176.5, 73.6], [186.7, 91.8],
                    [188.0, 84.1], [188.0, 85.9], [177.8, 81.8], [174.0, 82.5], [177.8, 80.5],
                    [171.4, 70.0], [185.4, 81.8], [185.4, 84.1], [188.0, 90.5], [188.0, 91.4],
                    [182.9, 89.1], [176.5, 85.0], [175.3, 69.1], [175.3, 73.6], [188.0, 80.5],
                    [188.0, 82.7], [175.3, 86.4], [170.5, 67.7], [179.1, 92.7], [177.8, 93.6],
                    [175.3, 70.9], [182.9, 75.0], [170.8, 93.2], [188.0, 93.2], [180.3, 77.7],
                    [177.8, 61.4], [185.4, 94.1], [168.9, 75.0], [185.4, 83.6], [180.3, 85.5],
                    [174.0, 73.9], [167.6, 66.8], [182.9, 87.3], [160.0, 72.3], [180.3, 88.6],
                    [167.6, 75.5], [186.7, 101.4], [175.3, 91.1], [175.3, 67.3], [175.9, 77.7],
                    [175.3, 81.8], [179.1, 75.5], [181.6, 84.5], [177.8, 76.6], [182.9, 85.0],
                    [177.8, 102.5], [184.2, 77.3], [179.1, 71.8], [176.5, 87.9], [188.0, 94.3],
                    [174.0, 70.9], [167.6, 64.5], [170.2, 77.3], [167.6, 72.3], [188.0, 87.3],
                    [174.0, 80.0], [176.5, 82.3], [180.3, 73.6], [167.6, 74.1], [188.0, 85.9],
                    [180.3, 73.2], [167.6, 76.3], [183.0, 65.9], [183.0, 90.9], [179.1, 89.1],
                    [170.2, 62.3], [177.8, 82.7], [179.1, 79.1], [190.5, 98.2], [177.8, 84.1],
                    [180.3, 83.2], [180.3, 83.2]
                    ],
                    markArea: {
                        silent: true,
                        itemStyle: {
                            color: 'transparent',
                            borderWidth: 1,
                            borderType: 'dashed'
                        },
                        data: [
                            [
                                {
                                    name: 'TransForm',
                                    xAxis: 'min',
                                    yAxis: 'min'
                                },
                                {
                                    xAxis: 'max',
                                    yAxis: 'max'
                                }
                            ]
                        ]
                    },
                    markPoint: {
                        data: [
                            { type: 'max', name: 'Max' },
                            { type: 'min', name: 'Min' }
                        ]
                    },
                    markLine: {
                        lineStyle: {
                            type: 'solid'
                        },
                        data: [{ type: 'average', name: 'Average' }, { xAxis: 170 }]
                    }
                }
            ]
        })
        let lineGan = echarts.init(this.$refs.lineGan)
        lineGan.setOption({
            title: {
                text: 'LOSS'
            },
            tooltip: {
                trigger: 'axis'
            },
            legend: {
                data: ['鉴别器LOSS', '生成器LOSS']
            },
            xAxis: {
                type: 'category',
                nameLocation: 'middle',
                data: [0, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1100, 1200, 1300, 1400, 1500, 1600]
            },
            yAxis: {
                name: 'LOSS'
            },
            series: [
                {
                    name: '生成器LOSS',
                    type: 'line',
                    color: 'rgb(118,141,209)',
                    datasetId: '生成器LOSS',
                    showSymbol: false,
                    data: [19, 24, 21, 20.1, 19.0, 18.3, 17.9, 16.0, 15.3, 11.5, 9.7, 3.2, 1.0, 0.8, 0.7, 0.34, 0.01],
                    encode: {
                        x: 'Year',
                        y: 'Income',
                        itemName: 'Year',
                        tooltip: ['Income']
                    }
                },
                {
                    name: '鉴别器LOSS',
                    type: 'line',
                    datasetId: '鉴别器LOSS',
                    color: 'rgb(167,214,145)',
                    showSymbol: false,
                    data: [23, 17.67, 16, 19.1, 12.0, 11.3, 13.9, 9.0, 8, 7, 6.99, 7.3, 2.8, 1.56, 0.79, 0.22, 0.09],
                    encode: {
                        x: 'Year',
                        y: 'Income',
                        itemName: 'Year',
                        tooltip: ['Income']
                    }
                }
            ]
        })
        let linePSNR = echarts.init(this.$refs.linePSNR)
        linePSNR.setOption({
            title: {
                text: 'PSNR'
            },
            tooltip: {
                trigger: 'axis'
            },
            xAxis: {
                type: 'category',
                nameLocation: 'middle',
                data: [0, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1100, 1200, 1300, 1400, 1500, 1600]
            },
            yAxis: {
                name: 'PSNR'
            },
            series: [
                {
                    name: 'PSNR',
                    type: 'line',
                    color: 'rgb(118,141,209)',
                    datasetId: 'PSNR',
                    showSymbol: false,
                    data: [3.3, 6.9, 9.89, 14, 8, 24, 24.6, 24.9, 24.34, 24.89, 25.8, 25.4, 24.89, 24.67, 24.99, 26.7, 25.78, 25.9],
                    encode: {
                        x: 'Year',
                        y: 'Income',
                        itemName: 'Year',
                        tooltip: ['Income']
                    }
                },

            ]
        })
        let barGAN = echarts.init(this.$refs.barGAN)
        barGAN.setOption({
            title: {
                text: 'Epochs and PSNR',
                subtext: '模型的效果'
            },
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'cross'
                }
            },
            toolbox: {
                show: true,
                feature: {
                    saveAsImage: {}
                }
            },
            xAxis: {
                type: 'category',
                boundaryGap: false,
                // prettier-ignore
                data: ['100', '200', '300', '400', '500', '600', '700', '800', '900', '1000', '1100', '1200', '1300', '1400', '1500', '1600', '1700', '1800', '1900', '2000']
            },
            yAxis: {
                type: 'value',
                axisLabel: {
                    formatter: '{value}'
                },
                axisPointer: {
                    snap: true
                }
            },
            visualMap: {
                show: false,
                dimension: 0,
                pieces: [
                    {
                        lte: 6,
                        color: 'green'
                    },
                    {
                        gt: 6,
                        lte: 8,
                        color: 'red'
                    },
                    {
                        gt: 8,
                        lte: 13,
                        color: 'green'
                    },
                    {
                        gt: 13,
                        lte: 17,
                        color: 'red'
                    },
                    {
                        gt: 17,
                        color: 'green'
                    }
                ]
            },
            series: [
                {
                    name: 'Electricity',
                    type: 'line',
                    smooth: true,
                    // prettier-ignore
                    data: [17, 15, 14, 15.6, 17.5, 19.6, 20.1, 18.67, 17, 18, 17.89, 18.23, 18.97, 24.7, 27.9, 26, 25.78, 24.12, 24.89, 25.71, 26],
                    markArea: {
                        itemStyle: {
                            color: 'rgba(255, 173, 177, 0.4)'
                        },
                        data: [
                            [
                                {
                                    name: 'down',
                                    xAxis: '700'
                                },
                                {
                                    xAxis: '900'
                                }
                            ],
                            [
                                {
                                    name: 'up and  down ',
                                    xAxis: '1400'
                                },
                                {
                                    xAxis: '1800'
                                }
                            ]
                        ]
                    }
                }
            ]
        })
        let linebarGAN = echarts.init(this.$refs.linebarGAN)
        function generateData(count) {
            let baseValue = Math.random() * 1000;
            let time = +new Date(2011, 0, 1);
            let smallBaseValue;
            function next(idx) {
                smallBaseValue =
                    idx % 30 === 0
                        ? Math.random() * 700
                        : smallBaseValue + Math.random() * 500 - 250;
                baseValue += Math.random() * 20 - 10;
                return Math.max(0, Math.round(baseValue + smallBaseValue) + 3000);
            }
            const categoryData = [];
            const valueData = [];
            for (let i = 0; i < count; i++) {
                categoryData.push(
                    echarts.format.formatTime('yyyy-MM-dd/nhh:mm:ss', time, false)
                );
                valueData.push(next(i).toFixed(2));
                time += 1000;
            }
            return {
                categoryData: categoryData,
                valueData: valueData
            };
        }
        const dataCount = 5e5;
        const data = generateData(dataCount);
        linebarGAN.setOption({
            title: {
                text: '数据量',
                left: 10
            },
            toolbox: {
                feature: {
                    dataZoom: {
                        yAxisIndex: false
                    },
                    saveAsImage: {
                        pixelRatio: 2
                    }
                }
            },
            tooltip: {
                trigger: 'axis',
                axisPointer: {
                    type: 'shadow'
                }
            },
            grid: {
                bottom: 50,
                left:40
            },
            dataZoom: [
                {
                    type: 'inside'
                },
                {
                    type: 'slider'
                }
            ],
            xAxis: {
                data: data.categoryData,
                silent: false,
                show: false,
                splitLine: {
                    show: false
                },
                splitArea: {
                    show: false
                }
            },
            yAxis: {
                splitArea: {
                    show: false
                }
            },
            series: [
                {
                    type: 'bar',
                    data: data.valueData,
                    // Set `large` for large data amount
                    large: true
                }
            ]
        })
    }
}
</script>

<style></style>