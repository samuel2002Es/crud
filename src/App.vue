<script>
  export default{
    data(){
      return{
        title: "GYM con vue",
        tareas: [],
        nuevaTarea: '',
      }
    },
    methods:{
      agregarTarea: function(){
        console.log("diste click");
        this.nuevaTarea = "";
      }
    },
    mounted() {
      console.log(tareas)
    },
  }
</script>

<template>
  <div class="container mt-5">
    <h3>{{ title }}</h3>
    <input type="text" class="form-control my-3" v-model="nuevaTarea">
    <button @click="agregarTarea" class="btn btn-primary">Agregar</button>
    <div class="mt-5">
      <div class="alert alert-primary" role="alert">esto es un alert</div>
    </div>
    <span>{{ nuevaTarea }}</span>
  </div>

</template>

<style scoped>

</style>
