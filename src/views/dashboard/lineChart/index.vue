<template>
    <div class="conter" ref="line">
    </div>
</template>
<script>
import echarts from 'echarts'
export default {
    name: 'lineChart',
    mounted(){
        console.log('1')
        let myLine = echarts.init(this.$refs.line)
        myLine.setOption({
            xAxis:{show:false,type:'category'},
            yAxis:{show:false},
            series:{
                type:'line',
                data:[10,40,79,89,60,80,90],
                lineStyle:{
                    color:'rgb(196,143,63)',
                    width:3
                },
                itemStyle:{
                        opacity:0
                    }
            },
            grid:{
                left:0,
                right:0,
                top:0,
                bottom:0
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