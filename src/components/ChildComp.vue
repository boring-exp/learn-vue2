<template>
    <div>
        <el-input v-model="message"></el-input>
        <el-input v-model="name"></el-input>
        <div>这是反转之后的值{{ reverseMsg }}</div>
    </div>
</template>

<script>
export default {
    name: 'ChildComp',

    data: function () {
        return {
            message: '',
            name: ''
        }
    },

    computed: {
        reverseMsg: function () {
            return this.message.split('').reverse().join('') + this.name
        }
    },

    watch: {
        name: function (newValue, oldValue) {
            console.log(newValue, oldValue)
        },
        message: {
            handler: function (newValue, oldValue) {
                console.log('message', newValue)
                console.log('message', oldValue)
            },
            immediate: true
        }
    },

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