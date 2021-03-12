<template>

  <div class="mt-4 align-items-center outputs card-body d-flex justify-content-between container ">
      <p :class="{done:todo.completed}" @click="todo.completed = !todo.completed">{{ todo.title }}</p>
    <div>
    <button class=" btn me-3 ms-3" @click="$emit('deleteBtn', todo._id)"><i class="far fa-trash-alt"></i></button> 
    
    </div>
  </div>
</template>

<script>
export default {
props:['todo']
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