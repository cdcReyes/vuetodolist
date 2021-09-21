<template>
    <div class="todo-container">
        <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
            <p>
                <input type="checkbox" v-on:change="markComplete">
                {{todo.title}}
                <button @click="$emit('del-todo', todo.id)" class="del">X</button>
                </p>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
    .todo-container{
        right: 0;
        left:0 ;
        margin-right: auto;
        margin-left: auto;

        max-width: 23em;

        background-image: url('~@/assets/listbg1.png');
        background-size: cover ;
       
    }

    .todo-item {
        padding: 10px;
        border-bottom: 1px;
        width: 100%;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del {
        background: #5b8397;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 90%;
        cursor: pointer;
        float: right;
    }
</style>