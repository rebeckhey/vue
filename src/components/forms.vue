<template>
 <div class="border-bottom bg-white">
     <form class="py-5 container" @submit.prevent="addTodo">
         <div class="row">
             <div class="col-7">
                 <div class="input-group">
      <input type="text" class="forms form-control" ref="error" placeholder="Add todo..." v-model="title">
      <button class="btn m-0 addBtn">ADD</button>
      </div>
      </div>
      <div class="col-5">
      <select class="form-control" v-model="choise" @change="$emit('sort', choise)">
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
    data(){
        return{
            title:'',
            choise:''
        }
        
    },
methods:{
    addTodo(){
        if(this.title !== ''){
            this.$emit('addTodo', this.title)
            this.$refs.error.classList.remove('is-invalid')
            this.title=''
        }
        else{
          this.$refs.error.classList.add('is-invalid')
        }
    }
}
}
</script>

<style>
.addBtn{
    background-color: cornflowerblue;
    padding: 0 2rem;
}

</style>