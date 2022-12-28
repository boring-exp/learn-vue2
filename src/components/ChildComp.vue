<template>
    <div>这是我们的子组件</div>
</template>

<script>
export default {
    name: 'ChildComp',

    // 生命周期函数
    beforeCreate() {
        console.log('beforeCreate')
    },

    created() {
        console.log('created')
    },

    beforeMount() {
        console.log('beforeMount')
    },

    mounted() {
        window.addEventListener('click', this.handleEvent)
        // TODO: 初始化组件的数据
        // 异步逻辑
        // const res = await xxxx();
        console.log('mounted')
    },

    beforeDestroy() {
        console.log('beforeDestroy')
    },

    destroyed() {
        // 取消事件的订阅
        console.log('destroyed')
        window.removeEventListener('click', this.handleEvent)
    },

    methods: {
        handleEvent() {
            console.log('吱吱吱')
        }
    }
}
</script>

<style lang="scss" scoped>
</style>