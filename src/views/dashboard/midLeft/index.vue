<template>
    <div style="margin-right: 5px;">
        <el-card>
            <div class="top">
                <el-menu class="el-menu-demo" mode="horizontal">
                    <el-menu-item index="1" style="color: black; font-size: larger;">模型种类</el-menu-item>
                    <el-menu-item index="4" style="color: black; font-size: larger;">图像分类</el-menu-item>
                </el-menu>
                <el-time-picker is-range v-model="value1" range-separator="至" start-placeholder="开始时间"
                    end-placeholder="结束时间" placeholder="选择时间范围" style="margin-top: 15px;">
                </el-time-picker>
                
            </div>
            <div class="bottom" ref="charts"></div>
        </el-card>
    </div>
</template>

<script>
import echarts from 'echarts'
export default {
    name: "midleft",
    data(){
        return {
            value1:0
        }
    },
    mounted(){
        let myCharts =  echarts.init(this.$refs.charts)
        myCharts.setOption({
            legend: {
    top: 'bottom'
  },
  toolbox: {
    show: true,
    feature: {
      mark: { show: true },
      dataView: { show: true, readOnly: false },
      restore: { show: true },
      saveAsImage: { show: true }
    }
  },
  series: [
    {
      name: 'Nightingale Chart',
      type: 'pie',
      radius: [50, 250],
      center: ['50%', '50%'],
      roseType: 'area',
      itemStyle: {
        borderRadius: 8
      },
      data: [
        { value: 40, name: '数据探索' },
        { value: 38, name: '医学数据增强' },
        { value: 32, name: '医学染色标准化' },
        { value: 30, name: '医学编码' },
        { value: 28, name: '医学影像识别' },
        { value: 26, name: '医疗影像分割' },
        { value: 22, name: '通用语义分割' },
        { value: 18, name: 'train' }
      ],

    }
  ]
        })
    }
}
</script>

<style>
.top{
    display: flex;
    justify-content: space-between;
}
.bottom{
    height: 800px;
    width: 100%;
}
</style>