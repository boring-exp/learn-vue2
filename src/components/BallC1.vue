<template>
    <div>这是我们的c1组件{{ val }}<el-button @send="send">发送数据给爷爷组件</el-button></div>
</template>
<script>
export default {
    name: 'BallC1',
    props: ['val'],
    methods: {
        send() {
            this.$emit('val', this.val - 1)
        }
    }
}
</script>