<template>
    <div class="conter" ref="line">
    </div>
</template>
<script>
import echarts from 'echarts'
export default {
    name: 'bar',
    mounted() {
        console.log('1')
        let myLine = echarts.init(this.$refs.line)
        myLine.setOption({
            xAxis: { show: false, type: 'category' },
            yAxis: { show: false },
            series: {
                type: 'bar',
                data: [
                    120,
                    {
                        value: 200,
                        itemStyle: {
                            color: '#a90000'
                        }
                    },
                    150,
                    80,
                    70,
                    110,
                    130
                ],
                color:"#f6da7b"

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