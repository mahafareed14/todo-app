<script>
    import TodoItem from './TodoItem.vue'
    export default {
        name: 'TodoList',
            components: {
                TodoItem
            },
        props: {
            msg: String
        },
        data: ()=> ({
            todo: '',
            data_todo: [], 
            }),
        methods: {
            addTodo() {
                if(this.todo.length != 0) {
                    let item = {
                    key: Math.random(),
                    message: this.todo
                    }
                this.data_todo.push(item);
                this.todo = '';
                }       
            },
            removeTodo(item_name) {
               this.data_todo = this.data_todo.filter(item => item.message!==item_name);
            },
            removeTodoAll() {
                this.data_todo = [];
            }
        }

    }
  </script>
<template>
    <div>
        <h1>{{ msg }}</h1>
        <input class ="input" type="text" 
               placeholder="Enter to do item" v-model="todo" v-on:keyup.enter="addTodo">
        <button @click="addTodo" class="button">Add</button>
        <button @click="removeTodoAll" class="button">Remove All Task</button>
        <div v-show="data_todo.length!=0" class="container">
            <div v-for="todo in data_todo" v-bind:key = "todo.key">
                <TodoItem :item_name = "todo.message" @remove="removeTodo(todo.message)"></TodoItem>
            </div>
        </div>
    </div>    
</template>

  
<style>
    .container {
        display: grid;
        overflow: auto;
        align-content: start;
        padding: 10px;
        margin-top: 10px;
        margin-left: 400px;
        width: 40%;
        height: 430px;
        border-radius: 50px;
        background-color: #a1b9d2;
    }
    .input {
        border: none;
        border-bottom: 2px solid rgb(52, 146, 222);
        padding: 16px 20px;
        text-align: left;
    }
    .button {
        background-color: #42a8ec; /* Blue */
        border: none;
        padding-left: 20px;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin-left:20px;
        margin-top: 10px;
    }
</style>
  