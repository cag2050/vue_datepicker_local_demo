<template>
    <div id="app">
        路由列表：<br/>
        <router-link to='/'>日期范围组件例子</router-link>
        <br/>
        <router-link to='/hello'>hello页面</router-link>
        <br/>
        <div>============以下是内容=============</div>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'App'
}
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
</style>
