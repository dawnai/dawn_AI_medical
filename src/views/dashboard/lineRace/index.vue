<template>
    <div class="conter" ref="line">
    </div>
</template>
<script>
import echarts from 'echarts'
export default {
    name: 'lineRace',
    mounted(){
        console.log('1')
        let myLine = echarts.init(this.$refs.line)
        myLine.setOption({
            xAxis:{show:false,type:'category'},
            yAxis:{show:false},
            series:[{
                type:'line',
                data:[10,40,50,70,78,90,91],
                lineStyle:{
                    color:'rgb(11,74,164)',
                    width:3
                },
                itemStyle:{
                        opacity:0
                    }
            },
            {
                type:'line',
                data:[2,7,9,20,60,80,100],
                lineStyle:{
                    color:'rgb(45,164,246)',
                    width:3
                },
                itemStyle:{
                        opacity:0
                    }
            },
            {
                type:'line',
                data:[20,30,80,86,92,96,120],
                lineStyle:{
                    color:'rgb(91,117,94)',
                    width:3
                },
                itemStyle:{
                        opacity:0
                    }
            },
        ],
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