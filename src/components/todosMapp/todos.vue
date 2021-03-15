<template>
  <div>
      <transition-group name="fade-slide">
<div v-for="todo in todos" :key="todo.id">
<todo v-if="value === ''" :todo="todo" @toggle="$emit('toogle')" @Deleted="$emit('deleteBtn', todo.id)"/>
<todo v-else-if="todo.completed === value" @toggle="$emit('toogle')" :todo="todo"  @Deleted="$emit('deleteBtn', todo.id)"/>
</div>      
</transition-group>


  </div>
</template>

<script>
import todo from './todo'
export default {
props:['todos', 'value'],
components:{ todo},
}
</script>

<style>
.fade-slide-enter-active, .fade-slide-leave-active{
    transition: all 0.5s ease;
}
.fade-slide-enter, .fade-slide-leave-to{
    opacity:0;
    transform: translateX(-50px)
}
</style>