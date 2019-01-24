<template>
    <div :class="['todo-item', todo.completed ? 'completed' : '']">
        <input type="checkbox" class="toggle" v-model="todo.completed">
        <label for="">{{todo.content}}</label>
        <button class="destory" @click="deleteTodo"></button>
    </div>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    methods: {
        deleteTodo() {
            this.$emit('del', this.todo.id)
        }
    }
}
</script>

<style lang="less" scoped>
    .todo-item {
        position: relative;
        background-color: #fff;
        font-size: 24px;
        border-bottom: 1px solid rgba(0,0,0,0.06);
        &:hover{
            .destory::after{
                content: 'x'
            }
        }           
        label{
            white-space: pre-line;
            word-break: break-all;
            padding: 15px 60px 15px 15px;
            margin-left: 45px;
            display: block;
            line-height: 1.2;
            transition: color 0.4s;
        }
        &.completed {
            label{
                color: #d9d9d9;
                text-decoration: line-through
            }
        }
                
    }
    .toggle{
        position: absolute;
        top: 0;
        bottom: 0;
        margin: auto 0;
        text-align: center;
        width: 50px;
        height: 30px;
        border: none;
        appearance: none;
        outline: none;
        &::after {
            content:url('../assets/images/unChecked.svg')
        }
            
        &:checked::after{
            content: url('../assets/images/checked.svg')
        }
    }
        
    .destory{
        position: absolute;
        top: 0;
        right: 0;
        width: 40px;
        margin: auto 0 11px;
        font-size: 30px;
        color: #cc9a9a;
        transition: color .2s ease-out;
        background-color: transparent;
        appearance: none;
        border: none;
        cursor: pointer;
        outline: none;
    }  
</style>