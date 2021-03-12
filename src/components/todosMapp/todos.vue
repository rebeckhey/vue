<template>
  <div>
<div v-for="todo in todos" :key="todo._id">

<todo :todo="todo" @deleteBtn="$emit('deleteBtn', todo._id)"/>

</div>
  </div>
</template>

<script>
import todo from './todo'
export default {
props:['todos'],
components:{ todo}
}
</script>

<style>

</style>