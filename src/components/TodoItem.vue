<template>
    <div class="todo-item">
        <div class="todo-item-left">
              <input type="checkbox" v-model="completed">
              <div v-if="!editing" @dblclick="editTodo" class="todo-item-label" :class="{ completed:completed }" >{{todo.title}}</div>
                  <input v-else class="todo-item-edit" type="text" v-model="title" @blur="doneEdit" @keyup.enter="doneEdit" v-focus>
          </div>
          <div class="remove-item" @click="removeTodo(index)">
              &times;
          </div>
    </div>
</template>

<script>
export default{
    name: 'todo-item',
    props: {
        todo: {
            type: Object,
            required: true,
        },
        index: {
            type: Number,
            required: true,
        }
    },
    data(){
        return{
            'id': this.todo.id,
            'title': this.todo.title,
            'completed': this.todo.completed,
            'editing': this.todo.editing
        }
    },
    methods:{
        removeTodo(index){
            this.$emit('removedTodo', index)
        },
        editTodo(){
            this.editing=true;
        },
        doneEdit(){
            this.editing=false;
            this.$emit('finishedEdit', {
                'index': this.index,
                'todo':{
                    'id': this.id,
                    'title': this.title,
                    'completed': this.completed,
                    'editing': this.editing
                }
            }
            
            )},
    }
}
</script>

<style>

</style>
