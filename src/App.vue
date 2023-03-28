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
        this.tareas.push({
          name: this.nuevaTarea,
          estado: false
        });
        /* console.log(this.tareas); */
        this.nuevaTarea = "";
        localStorage.setItem('gym-vue', JSON.stringify(this.tareas));
      },
      editarTarea: function(index){
        this.tareas[index].estado = true;
        console.log("editar"+ index);
        localStorage.setItem('gym-vue', JSON.stringify(this.tareas));
      },
      eliminar: function(index){
        /* splice recibe dos parametros, el primero en el indice a eliminar, y luego el numero de datos a eliminar */
        this.tareas.splice(index,1)
        localStorage.setItem('gym-vue', JSON.stringify(this.tareas));
      }
    },
    /* esta funcion es unica y se ejecuta luego luego que carga el js */
    created: function () {
      let datosDB = JSON.parse(localStorage.getItem('gym-vue'));
      console.log(datosDB)
      if (datosDB === null) {
        this.tareas = [];
      }else{
        this.tareas = datosDB;
      }
    }
  }
</script>

<template>
  <div class="container mt-5">
    <h3>{{ title }}</h3>
    <input type="text" class="form-control my-3" v-model="nuevaTarea" v-on:keyup.enter="agregarTarea">
    <button @click="agregarTarea" class="btn btn-primary">Agregar</button>
    <div v-for="(item, index) of tareas" :key="item.index">
      <div :class="['alert', item.estado ? 'alert-success' : 'alert-danger']" role="alert">
        <div class="d-flex justify-content-between align-items-center">
          <div>
            {{ index }} -- {{ item.name }} -- {{ item.estado }}
          </div>
          <div >
            <button class="btn btn-success btn-sm" @click="editarTarea(index)">Ok</button>
            <button class="btn btn-danger btn-sm" @click="eliminar(index)">x</button>
          </div>
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>
