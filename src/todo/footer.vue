<template>
    <div id="appfooter">
        <span>by {{author}}</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            author: 'https://github.com/befriend1314'
        }
    }
}
</script>

<style lang="less" scoped>
    #appfooter{
        margin-top: 40px;
        text-align: center;
        color: #000;
        font-size: 12px;
        text-shadow:chocolate 0 1px 0  #ffffff
    }
</style>