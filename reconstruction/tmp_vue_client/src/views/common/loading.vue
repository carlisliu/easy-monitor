<style scoped lang="less">
    p {
        font-size: 1.0em;
        color: #3091f2;
    }
    .spin-icon-load{
        animation: ani-spin 1s linear infinite;
    }
    @keyframes ani-spin {
        from { transform: rotate(0deg);}
        50%  { transform: rotate(180deg);}
        to   { transform: rotate(360deg);}
    }
    .spin-col{
        height: 100px;
        position: relative;
        justify-content:center;
        align-items:center;
        display:-webkit-flex;
    }
</style>
<style>
    .spin-col .ivu-alert-error {
        border: 0px
    }
</style>

<template>
<div class="spin-col" v-if="notdone">
    <Spin fix v-if="!error">
        <Icon type="load-c" size=18 class="spin-icon-load"></Icon>
        <div><p>{{ loadingMsg || defaultLoadingMsg }}</p></div>
    </Spin>

     <Alert type="error" show-icon v-if="error">
        Inner Error
        <span slot="desc">
            Detail: {{ error }}
        </span>
    </Alert>
</div>
</template>

<script>
    export default {
        data() {
            return {
                defaultLoadingMsg: 'Loading...'
            }
        },
        props: ['notdone', 'loadingMsg', 'error']
    }
</script>