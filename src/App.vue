<template>
  <div id="app">
   <headder title="TODOLIST"/>
  <forms />
  <todos :todos="todos" @deleteBtn="deleteBtn" />
  </div>
</template>

<script>
import headder from './components/headder'
import forms from './components/forms'
import todos from './components/todosMapp/todos'

export default {
  name: 'App',
  components: {
   headder,
   forms,
   todos
  },
  data(){
    return {
      todos:[
        {_id:'1', title:'Städa', completed:true},
         {_id:'2', title:'Laga mat', completed:false},
          {_id:'3', title:'Diska', completed:false},
           {_id:'4', title:'Rensa', completed:false}
      ]
    }
  },
  methods:{
    deleteBtn(id){
      this.todos = !this.todos.filter(todo => todo._id !== id) // döper varje objekt till todo. 
      // Kollar om: todo._id inte matchar id som har tryckts på, matchar den så ska den ligga kvar, matchar den inte
      //ska den inte ligga kvar. (filter loopar igenom arrayen, sen ska den ha condition true eller false)

    }
  }
}
</script>

<style>

</style>
