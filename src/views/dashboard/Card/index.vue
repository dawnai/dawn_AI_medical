<template>
    <div style="padding: 0px 5px;">
        <el-card>
            <div class="header">
                <span style="color: rgb(159,210,244);font-weight: bolder;">{{title}}</span>
                <svg t="1691462022464" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                    p-id="6103" width="16" height="16">
                    <path
                        d="M512 0C229.2 0 0 229.2 0 512s229.2 512 512 512 512-229.2 512-512S794.8 0 512 0z m-32 769V353c0-17.7 14.3-32 32-32s32 14.3 32 32v416c0 8.8-3.6 16.8-9.4 22.6-5.8 5.8-13.8 9.4-22.6 9.4-17.7 0-32-14.3-32-32z m64-543.5c0 8.8-3.6 16.8-9.4 22.6-5.8 5.8-13.8 9.4-22.6 9.4-17.7 0-32-14.3-32-32v-1c0-17.7 14.3-32 32-32s32 14.3 32 32v1z"
                        p-id="6104" fill="#9fd2f4"></path>
                </svg>
            </div>
            <div class="mider">
                <h2 style="color: rgb(239,173,1);">{{number}}</h2>
                <slot name="echarts"></slot>
            </div>
            <div class="footer">
                <span style="color: rgb(159,210,244); ">截止时间:         {{ time }} </span>
            </div>
        </el-card>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props:['title','number','time']
}
</script>
<style scoped>
.header {
    color: rgb(172, 172, 173);
    display: flex;
    justify-content: space-between;
}
.footer{
   border-top: 1px solid #f6da7b;
   padding-top: 10px;
}
</style>
