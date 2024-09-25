<template>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <thead>
          <tr>
            <th>Código</th>
            <th>Nombre</th>
            <th>Stock</th>
            <th>Precio</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="juego in juegos" :key="juego.codigo">
            <td>{{ juego.codigo }}</td>
            <td>{{ juego.nombre }}</td>
            <td>{{ juego.stock }}</td>
            <td>{{ formatearPrecio(juego.precio) }}</td>
            <td>
              <button @click="cambiarStock(juego.codigo, juego.stock + 1)">+</button>
              <button @click="cambiarStock(juego.codigo, juego.stock - 1)" :disabled="juego.stock <= 0">-</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import { mapState, mapActions } from 'vuex';
  
  export default {
    computed: {
      ...mapState(['juegos'])
    },
    methods: {
      ...mapActions(['modificarStock']),
      formatearPrecio(precio) {
        return new Intl.NumberFormat('es-CL', { style: 'currency', currency: 'CLP' }).format(precio);
      },
      cambiarStock(codigo, nuevoStock) {
        if (nuevoStock >= 0) {
          this.modificarStock({ codigo, nuevoStock });
        }
      }
    }
  };
  </script>
  
  <style scoped>
  table {
    width: 100%;
  }
  th, td {
    padding: 10px;
    text-align: center;
  }
  </style>
  