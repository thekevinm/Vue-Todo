<template>
    <div v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete" />
            {{ todo.title }}
            <button @click="$emit('del-todo', todo.id)" class="delete">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "ToDoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    div {
        /* border: 1px solid red; */
        width: 100%;
        height: 25px;
        font-size: 20px;
    }

    .is-complete {
        text-decoration: line-through;
    }

    button {
        float: right;
        border-radius: 50%;
        background-color: rgba(255, 0, 0, 0.788);
        outline: none;
        height: 23px;
    }
</style>


