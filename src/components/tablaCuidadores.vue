<template>
  <div class="tbCuidadores">
    <fieldset>
      <legend>Tabla de Cuidadores</legend>
      <table>
        <tr>
          <th>id</th>
          <th>nombre</th>
          <th>fecha Nacimiento</th>
        </tr>
        <tr v-for="cuidador in cuidadores" :key="cuidador.idCuidador">
          <td>{{ cuidador.idCuidador }}</td>
          <td>{{ cuidador.nombreCuidador }}</td>
          <td>{{ cuidador.fechaNacimientoC }}</td>
        </tr>
      </table>
    </fieldset>

    <router-view />
  </div>
</template>

<script>
export default {
  name: "tablaCuidadores",
  props: {
    cuidadores: {
      type: Array,
    }
  },
  methods: {},
};
</script>

<style scoped>
.tbCuidadores {
  padding: 5%;
  text-align: center;
}
table {
  border: 1px solid #000;
  margin: auto;
  padding: 1 px;
}
th {
  border: 1px solid #000;
}
tr,
td {
  width: 20%;
  text-align: left;
  vertical-align: top;
  border: 1px solid #000;
}
</style>