<template>
  <nav class="head text-center pb-5 pt-5 ">
<h1 class="rubrik">{{ title }}</h1>
  </nav>
</template>

<script>
export default {
props:['title']
}
</script>

<style>
.head{
    background-color: cornflowerblue;
}
.rubrik{
    font-size: 3rem;
}
</style>