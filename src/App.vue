<template>
    <div id="app">
        <!-- 显示的是当前路由地址所对应的内容 -->
        <keep-alive exclude="Detail">
            <router-view />
        </keep-alive>
    </div>
</template>

<script>
// app.vue是一个单文件组件
export default {
    name: 'App'
}
</script>

<style></style>
