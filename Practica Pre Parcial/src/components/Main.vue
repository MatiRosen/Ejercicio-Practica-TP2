<template>
    <div>
      <h1>Lista de tareas</h1>
      <table>
        <tr>
          <td>Tarea</td>
          <td>Completada</td>
          <td>Eliminar</td>
        </tr>
        <tr v-for="tarea in filtrarTareas()" :key="tarea.id">
          <td>{{ tarea.descripcion }}</td>
          <td><input type="checkbox" v-model="tarea.completa"></td>
          <td>
            <Item
              :descripcion="tarea.descripcion"
              :completa="tarea.completa"
              @eliminarItem="eliminar(tarea)"
            />
          </td>
        </tr>
      </table>
      <br>
      <h2>Filtrar:</h2>
      <table>
        <tr>
          <td>Completadas</td>
          <td>Incompletas</td>
        </tr>
        <tr>
          <td><input type="checkbox" v-model="mostrarCompletadas"></td>
          <td><input type="checkbox" v-model="mostrarIncompletas"></td>
        </tr>
      </table>
      <br>
      <h2>Agregar tarea nueva: </h2>
      <Tarea @agregarTarea="agregar($event)" />
    </div>
  </template>
  
  <script>
  import Item from "./Item.vue";
  import Tarea from "./Tarea.vue";
  export default {
    components: {
      Tarea,
      Item,
    },
    data() {
      return {
        tareas: [
          { id: 0, descripcion: "Programar el bot para que me haga el parcial", completa :false },
          { id: 1, descripcion: "Programar el bot que hackea el sistema para ponerme 10 en todo", completa: true },
        ],
        mostrarCompletadas: false,
        mostrarIncompletas: false,
      };
    },
    methods: {
      agregar(tarea) {
        this.tareas.push({... tarea});
      },
      eliminar(tarea) {
        this.tareas = this.tareas.filter(
          (t) => t.id != tarea.id
        );
      },
      filtrarTareas() {
        if (this.mostrarCompletadas && !this.mostrarIncompletas) {
          return this.tareas.filter((t) => t.completa);
        } else if (!this.mostrarCompletadas && this.mostrarIncompletas) {
          return this.tareas.filter((t) => !t.completa);
        } else {
          return this.tareas;
        }
    },
    },
  };
  
  </script>
  
  <style></style>
  