<template>
    <div>
        <form @submit="addTodo">
                <input type="text" v-model="title" name="title" placeholder="What Todo?" id="addTodo" />
                <button type="submit" class="SubBtn">Submit</button>
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            var addInput = document.getElementById("addTodo").value;

            e.preventDefault();

            if (addInput !== '') {
                var newTodo = {
                    id: uuid.v4(),
                    title: this.title,
                    completed: false
                }
                // Send to parent
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
}
</script>

<style scoped>
div {
    display: flex;
    justify-content: center;
    margin: auto;
    margin-top: 15px;
}

input {
    width: 500px;
    height: 29px;
    padding-left: 5px;
    outline: none;
}

button {
    outline: none;
    height: 28px;
    background-color: silver;
    border: none;
}

@media (max-width: 1000px) {
    input {
        width: 200px;
    }
}
</style>


