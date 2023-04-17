<template>
    <div>
      <button @click="eliminar">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    emits: ["eliminarItem"],
    props: ["descripcion", "completa"],
    data() {
      return {};
    },
    methods: {
      eliminar() {
        this.$emit("eliminarItem");
      },
    },
  };
  </script>
  
  <style></style>
  