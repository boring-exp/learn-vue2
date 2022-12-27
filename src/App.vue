<template>
  <!-- 0.v-bind -->
  <div :id="idName">
    <!-- 1.v-html -->
    <span v-html="message"></span>
    <!-- <span>{{ msg }}</span> -->
    <el-button :disabled="false" v-on:click="createHelloMsg">确定</el-button>
    <!-- 4.v-on -->
    <el-button @click="createHelloMsg">确定（简写）</el-button>

    <!-- 2.v-if/v-show -->
    <div v-if="isShow">😄</div>
    <div v-else>😂</div>

    <!-- 2.v-if/v-show -->
    <div v-show="isShow">😄</div>

    <!-- 3.v-for -->
    <div v-for="(names, index) in nameArr" :key="index">
      {{ index + 1 }} . {{ names }}
    </div>

    <!-- 5.v-model 创建双向绑定-->
    <el-input v-model="info"></el-input>
  </div>
</template>

<script>
const msg = '<h1>哈哈哈</h1>';

export default {
  // 预定义属性
  name: 'App',
  // 组件当中所有的响应式数据
  data: function () {
    return {
      message: msg,
      idName: 'app',
      isShow: true,
      nameArr: ['pjw', 'ss', 'hello'],
      info: '123456123'
    }
  },
  // 方法
  methods: {
    createHelloMsg() {
      console.log(this.info)
    },
  },

  // 生命周期函数之一
  mounted() {
    // 当 当前组件 被挂载时，出发执行
    setTimeout(() => {
      this.isShow = false
    }, 3000)
  },
}
</script>

<style lang="scss">
html,
body {
  margin: 0;
  padding: 0;
}
</style>
