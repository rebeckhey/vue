<template>
  <div id="app">
   <headder title="TODOLIST"/>
  <forms @addTodo="add" @sort="sortTodos"/>
  <todos :value="sort" :todos="todos" @deleteBtn="deleteBtn" @toggle="fetchtodos" />
  </div>
</template>

<script>
import headder from './components/headder'
import forms from './components/forms'
import todos from './components/todosMapp/todos'
// import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'App',
  components: {
   headder,
   forms,
   todos
  },
  data(){
    return {
      // todos:[
      //   {id:'1', title:'Städa', completed:true},
      //    {id:'2', title:'Laga mat', completed:false},
      //     {id:'3', title:'Diska', completed:false},
      //      {id:'4', title:'Rensa', completed:false}
      // ],
      todos:[],
      sort:''
    }
  },
  methods:{
    deleteBtn(id){
      // this.todos = this.todos.filter(todo => todo.id !== id) // döper varje objekt till todo. 
      // Kollar om: todo._id inte matchar id som har tryckts på, matchar den så ska den ligga kvar, matchar den inte
      //ska den inte ligga kvar. (filter loopar igenom arrayen, sen ska den ha condition true eller false)
      fetch(`http://localhost:3000/todos/${id}`, {
          method: 'DELETE'
      })
      .then(res => {
        if(res.status === 200){ 
          this.fetchtodos()
        }
      })
    },
    add(title){
      // let todo = {
      //   id:uuidv4(),
      //   title, 
      //   completed:false
      // }
      // this.todos.unshift(todo)
      fetch('http://localhost:3000/todos',{
        method: 'POST',
        headers: {
          'content-type': 'application/json; charset= UTF-8'
          },
          body: JSON.stringify({
            title,
            completed:false
          })
      })
      .then(res => {
        if(res.status === 201){
          this.fetchtodos()
        }
      })
    },
    sortTodos(val){
      switch(val){
        case 'false':
        this.sort = false
        break;
        case 'true':
          this.sort = true
          break;
        default:
        this.sort=''
      }
    },
    fetchtodos(){
      fetch('http://localhost:3000/todos')
      .then(res => res.json())
      .then(data => {
        this.todos= data
      })
    }
  },
  created(){
      this.fetchtodos()
    }
}
</script>

<style>

</style>
