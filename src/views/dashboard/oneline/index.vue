<template>
    <div class="conter" ref="line">
    </div>
</template>
<script>
import echarts from 'echarts'
export default {
    name: 'lineRace',
    mounted() {
        console.log('1')
        let myLine = echarts.init(this.$refs.line)
        myLine.setOption({
            xAxis: {
                min: 0,
                max: 100,
                show: false
            },
            yAxis: {
                show: false,
                type: 'category'
            },
            series: {
                type: 'bar',
                data: [80],
                barwidth: 80,
                barWidth: 10,
                color: 'yellowgreen',
                // 背景颜色
                showBackground: true
            },
            grid: {
                left: 0,
                right: 0,
                top: 0,
                bottom: 0
            }
        })
    }
}
</script>
<style>
.conter {
    height: 80px;
    width: 100%;
}
</style>