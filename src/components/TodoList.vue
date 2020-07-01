<template>
  <div class="todo-form">
      <input type="text" class="todo-input" placeholder="Task..." v-model="newTodo" @keyup.enter="addTodo">
      <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" :index="index" @removedTodo="removeTodo" @finishedEdit="finishedEdit">
      </todo-item> <!-- END todo-item -->
  </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
  name: 'TodoList',
  components: {
      TodoItem,
  },
  data () {
    return {
     newTodo: '',
     idForTodo: 3,
     todos: [
       {
         'id': 1,
         'title': 'Get the car', 
         'completed': false,
         'editing': false,
       },
       {
         'id': 2,
         'title': 'Buy fruits', 
         'completed': false,
         'editing': false,
       }
     ]
    }
  },

  directives: {
    focus:{
        inserted: function(el){
            el.focus()
        }
    }   
  },  

  methods: {
    addTodo(){
        if(this.newTodo.trim().length == 0){
            return
        }
      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
        editing: false,
      })
      this.newTodo=''
      this.idForTodo++

    },

    editTodo(todo){
        todo.editing=true;
    },

    doneEdit(todo){
        todo.editing=false;
    },

    removeTodo(index){
        this.todos.splice(index, 1)
    },
    finishedEdit(data){
        this.todos.splice(data.index, 1, data.todo)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style  lang="scss">
// .todo-form{
//     background: floralwhite;
// }
.todo-input{
  width: 100%;
  padding: 10px 20px;
  font-size: 18px;
  margin-bottom: 18px;
  

  &:focus{
    outline: 0;
  }

}

.todo-item{
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.remove-item {
    cursor: pointer;
    margin-left: 14px;
    &:hover{
        color: black;
    }
}
.todo-item-left {
    display: flex;
    align-items: center;
}

.todo-item-label {
    padding: 10px;
    border: 1px solid white;
    margin-left: 12px;
}

.todo-item-edit {
    font-size: 16px;
    color: #2c3e50;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    // background: crimson;

    // &:focus{
    //     outline: none;
    // }


.completed { 
    text-decoration: line-through;
    color: grey
}    
}
   
</style>