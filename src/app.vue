<template>
   <div id="app">
       <div id="cover"></div>
       <Header></Header>
       <Todo></Todo>
        <Footer></Footer>
   </div>
</template>

<script>
import Header from './todo/header.vue'
import Footer from './todo/footer.vue'
import Todo from './todo/todo.vue'
export default {
    components: {
        Header,
        Footer,
        Todo
    }
}
</script>

<style lang="less" scoped>
    #app{
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
    }
    #cover{
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        background-color: #fff;
        opacity: .6;
        z-index: -1;
    }
</style>
