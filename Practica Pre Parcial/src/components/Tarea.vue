<template>
    <div>
      <p>
        Descripcion: <input v-model="tarea.descripcion" />
        <button @click="agregarTarea">Agregar</button>
      </p>
    </div>
  </template>
  
  <script>
  export default {
    emits: ["agregarTarea"],
    data() {
      return {
        id: 2,
        tarea: { id: 0, descripcion: "", completa: false },
      };
    },
    methods: {
      agregarTarea() {
        this.tarea.id = this.id++;
        this.$emit("agregarTarea", this.tarea);
      },
    },
  };
  </script>
  
  <style></style>
  