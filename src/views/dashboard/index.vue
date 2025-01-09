<template>
  <div>
    <el-row>
      <el-col :span="18">
        <div style="position: relative; height: 100%;width: 100%;">
          <!-- 主页插画 -->
          <!-- <img src="./img/1.png" alt="" style="width: 100%;height: 100%; ">
           -->
          <div style="width: 80%;height: 80%;">
            <mylott></mylott>
          </div>

          <div class="welcome">
            <h1 style="font-size: 60px;">欢迎使用</h1>
            <br>
            <h1 style="margin-top: -25px; font-size:60px;">赛宝人工智能</h1>
            <br>
            <h1 style="margin-top: -25px; font-size:60px;">医疗影像应用测试系统</h1>
            <br>
            <br>
            <h3 style="margin-top: -60px;">Welcome to the CEPREI-AIMITS.</h3>
          </div>
        </div>
      </el-col>

    </el-row>

    <div class="header">
      <el-row>
        <el-col :span="6">
          <Card title="访问量" number="20k" time="2023/06/06">
            <template slot="echarts">
              <lineChart />
            </template>
          </Card>
        </el-col>
        <el-col :span="6">
          <Card title="在线用户" number="2489" time="2023/06/06">
            <template slot="echarts">
              <bar />
            </template>
          </Card>
        </el-col>
        <el-col :span="6">
          <Card title="模型数量" number="108" time="2023/06/01">
            <template slot="echarts">
              <lineRace />
            </template>
          </Card>
        </el-col>
        <el-col :span="6">
          <Card title="用户满意度" number="97%" time="2023/08/06">
            <template slot="echarts">
              <oneline />
            </template>
          </Card>
        </el-col>
      </el-row>
    </div>
    <div class="mider">
      <el-row>
        <el-col :span="18">
          <midLeft />
        </el-col>
        <el-col :span="6">
          <midRight />
        </el-col>
      </el-row>

    </div>
    <div class="footer">
      <textP></textP>
    </div>
  </div>
</template>
<script>
import Card from './Card'
import lineChart from './lineChart'
import bar from './bar'
import lineRace from './lineRace'
import oneline from './oneline'
import midRight from './midRight'
import midLeft from './midLeft'
import textP from './textP'
import mylott from './mylott'
export default {
  name: 'Dashboard',
  components: {
    Card,
    lineChart,
    bar,
    lineRace,
    oneline,
    midLeft,
    midRight,
    textP,
    mylott
  }
}
</script>
<style scoped>
/* 在线链接服务仅供平台体验和调试使用，平台不承诺服务的稳定性，企业客户需下载字体包自行发布使用并做好备份。 */
@font-face {
  font-family: 'fuck';
  src: url('~@/assets/AlimamaFangYuanTiVF-Thin.ttf') format('truetype');
}
h1{
  font-family:'fuck';
  font-weight:bold;
  
  
}
.header {
  margin: 10px 0px;
}

.welcome {
  position: absolute;
  top: 100px;
  right: -300px;
  background: linear-gradient(45deg, rgb(245, 72, 138), rgb(2, 176, 244));
  -webkit-background-clip: text;
  color: transparent;
}

.welcome:hover {
  background: linear-gradient(45deg, rgb(2, 176, 244), rgb(245, 72, 138));
  -webkit-background-clip: text;
  color: transparent;
}
</style>







