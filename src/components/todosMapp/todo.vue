<template>

  <div class="mt-4 align-items-center outputs card-body d-flex justify-content-between container ">
      <p :class="{ done:todo.completed }" @click="toggleCompleted">{{ todo.title }}</p>
    <div>
    <button class=" btn me-3 ms-3" @click="Deleted"><i class="far fa-trash-alt"></i></button> 
    
    </div>
  </div>
</template>

<script>
export default {
props:['todo'],
methods:{
    toggleCompleted(){
         fetch(`http://localhost:3000/todos/${this.todo.id}`,{
             method: 'PATCH', 
             headers: {
          'content-type': 'application/json; charset= UTF-8'
          },
             body:JSON.stringify ({
                completed: !this.todo.completed
             })
         })
          .then(res => {
              if(res.status === 200){
                  this.$emit('toggle')
              }
          })
    },
    Deleted(){
    if(this.todo.completed){
this.$emit('deleteBtn', this.todo.id)}
else{
  alert('todon är inte klar!')
}
  }
   
}

}
</script>

<style>
i {
    font-size: 1.5rem;
    color: cornflowerblue;
}

.outputs{
    border: 1px solid lightgrey;
    width: 30%;
    border-radius:5px;
    cursor: pointer;
}
p{
    font-size: 1.5rem;
    margin-bottom: 0;
    flex: 1;
}
.done{
    text-decoration:line-through;
    color:lightgrey
}
</style>