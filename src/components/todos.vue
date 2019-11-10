<template>
    <div class="container">

        <div class="input-section">
           <input type="text" v-model="newTodo" v-on:keydown.enter="addTodo">
            <button @click="addTodo">Add</button>
        </div>

        <div class="todo-lists">
           <ul class="todos">
                <li v-for="todo in todos" :class="{ 'removed' : todo.completed }" >
                    <div class="checkbox"  v-if="!todo.edited">
                        <label @dblclick="editTodo(todo)">
                            <input type="checkbox" v-model="todo.completed">
                            {{todo.title}}
                        </label>
                        <button class="removeBtn" @click="removeTodo(todo)">X</button>
                    </div>
                    <input class="edit" type="text"
                           v-if="todo.edited"
                           v-model="newTodo"
                           @blur="doneEdit(todo)"
                           v-on:keydown.enter="doneEdit(todo)"
                    >
                </li>
           </ul>
        </div>

        <button @click="removeCompletedTodos">Remove Todos</button>

    </div>
</template>

<script>
    export default {
      data: function(){
        return{
          newTodo: '',
          todos: [],
          editedTodo: '',
        }
      },
      methods: {
        addTodo: function(){
          var value = this.newTodo && this.newTodo.trim()
          if(!value){
            return
          }
          this.todos.push({
            id: this.todos.length,
            title: value,
            completed: false,
            edited: false
          })
          this.newTodo = ''
        },
        editTodo: function(todo){
            todo.edited = !todo.edited
        },
        doneEdit: function(todo){
            let edit = this.newTodo && this.newTodo.trim()
            todo.title = edit
            todo.edited = false
        },
        removeTodo: function(todo){
            this.todos.splice(this.todos.indexOf(todo), 1)
        },
        removeCompletedTodos: function(){
            let completed = this.todos.filter(x => !x.completed)
            this.todos = completed
        }
      }
    }
</script>

<style>
    .checkbox {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
    }

    .removed {
        color: gray;
    }

    .removed label {
        text-decoration: line-through;
    }

    .removeBtn {
        background-color: transparent;
    }

</style>
