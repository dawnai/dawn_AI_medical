<template>
    <div>
        <el-table :data="tableData" style="width: 100%" :row-class-name="tableRowClassName" >
            <el-table-column prop="date" label="日期" width="100" align="center">
            </el-table-column>
            <el-table-column prop="name" label="模型名称" width="100" align="center">
            </el-table-column>

            <el-table-column prop="state" label="状态" align="center">
                <template slot-scope="{row,index}">
                    <i v-if="row.state == 'ing'" class="el-icon-loading" style="color: green; font-size: 20px;"></i>
                    <i v-if="row.state == 'warn'" class="el-icon-warning" style="font-size: 20px;"></i>
                    <i v-if="row.state == 'down'" class="el-icon-circle-check" style="color: #409EFF;font-size: 20px;"></i>
                </template>
            </el-table-column>

            <el-table-column prop="rate" label="进度" align="center"> 
                <template slot-scope="{row,index}">
                    <el-progress type="circle" :percentage="row.rate"  :status="row.stateInfo"></el-progress>
                </template>

            </el-table-column>
            <el-table-column prop="option" label="操作" align="center">
                <template slot-scope="{row,index}">

                    <el-tooltip content="查看内容" placement="top">
                        <el-button icon="el-icon-view" v-if="row.state == 'down'" type="primary"></el-button>
                    </el-tooltip>

                    <el-tooltip content="暂停训练" placement="top">
                        <el-button icon="el-icon-video-pause" v-if="row.state == 'ing'" type="warning"></el-button>
                    </el-tooltip>

                    <el-tooltip content="继续训练" placement="top">
                        <el-button icon="el-icon-video-play" v-if="row.state == 'warn'" type="warning"></el-button>
                    </el-tooltip>

                    <el-tooltip content="删除任务" placement="top">
                        <el-button icon="el-icon-delete" type="danger"></el-button>
                    </el-tooltip> 
                </template>

            </el-table-column>
        </el-table>
    </div>
</template>

<script>
export default {
    name: 'training',
    methods: {
        tableRowClassName({ row, rowIndex }) {
            if (rowIndex === 1) {
                return 'warning-row';
            } else if (rowIndex === 3) {
                return 'success-row';
            }
            return '';
        },
        fuck(row) {
            console.log(row)
        }
    },
    data() {
        return {
            tableData: [{
                date: '2023-05-02',
                name: 'GKMNet',
                state: 'ing',
                stateInfo: '',
                rate: 20,
                option: ''
            }, {
                date: '2023-05-04',
                name: 'LSTM',
                state: 'warn',
                stateInfo: 'warning',
                rate: 60,
            }, {
                date: '2023-05-01',
                name: 'DCGAN',
                state: 'ing',
                stateInfo: '',
                rate: 60,
            }, {
                date: '2023-05-03',
                name: 'LIIF',
                state: 'down',
                rate: 100,
                stateInfo: 'success',
            }]
        }
    }
}
</script>

<style>
.el-table .warning-row {
    background: oldlace;
}

.el-table .success-row {
    background: #f0f9eb;
}
</style>