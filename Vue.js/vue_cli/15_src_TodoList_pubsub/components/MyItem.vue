<template>
    <li>
        <label>
        <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>
        <!-- 如下代码也能实现功能，但是不太推荐，因为有点违反原则，因为修改了 props -->
        <!-- <input type="checkbox" v-model="todo.done"/> -->
        <span>{{ todo.title }}</span>
        </label>
        <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
    </li>
</template>

<script>
import pubsub from 'pubsub-js'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'MyItem',
    // 声明接收 todo 对象
    props: ['todo', 'checkTodo', 'deleteTodo'],
    methods: {
        // 勾选 or 取消勾选
        handleCheck(id) {
            // 通知 App 组件将对应的 todo 对象的 done 值取反
            this.$bus.$emit('checkTodo', id);  
        },
        handleDelete(id) {
            if (confirm('确定删除吗？')) {
                // this.$bus.$emit('deleteTodo', id);
                pubsub.publish('deleteTodo', id); // 消息名 数据
            }
        }
    }
}
</script>

<style scoped>
    /*item*/
    li {
        list-style: none;
        height: 36px;
        line-height: 36px;
        padding: 0 5px;
        border-bottom: 1px solid #ddd;
    }

    li label {
        float: left;
        cursor: pointer;
    }

    li label li input {
        vertical-align: middle;
        margin-right: 6px;
        position: relative;
        top: -1px;
    }

    li button {
        float: right;
        display: none;
        margin-top: 3px;
    }

    li:hover button {
        display: block; 
    }

    li:before {
        content: initial;
    }

    li:last-child {
        border-bottom: none;
    }

    li:hover {
        background-color: #ddd;
    } 
</style>