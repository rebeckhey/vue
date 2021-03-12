<template>
 <div class="border-bottom bg-white">
     <form class="py-5 container">
         <div class="row">
             <div class="col-7">
                 <div class="input-group">
      <input type="text" class="form-control" placeholder="Add todo...">
      <button class="btn m-0 addBtn">ADD</button>
      </div>
      </div>
      <div class="col-5">
      <select class="form-control">
          <option value="">Show all</option>
          <option value="false">Show uncompleted</option>
          <option value="true">Show completed</option>
      </select>
      </div>
      </div>
      </form>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.addBtn{
    background-color: cornflowerblue;
    padding: 0 2rem;
}

</style>