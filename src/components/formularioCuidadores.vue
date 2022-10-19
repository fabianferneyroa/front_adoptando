<template>
  <div class="formCuidador">
    <fieldset>
      <legend>Formulario Registro Cuidadores</legend>
      <form @submit.prevent="guardar">
        <label for="idCuidador">id cuidador</label><br />
        <input
          type="number"
          name="idCuidador"
          id="idCuidador"
          v-model="cuidador.idCuidador"
        /><br />

        <label for="nombre">nombre</label><br />
        <input
          type="text"
          name="nombre"
          id="nombre"
          v-model="cuidador.nombreCuidador"
        /><br />

        <label for="fechaNacimiento">fechde nacimiento</label><br />
        <input
          type="date"
          name="fechaNacimiento"
          id="fechaNacimiento"
          v-model="cuidador.fechaNacimientoC"
        /><br />

        <button type="submit">Guardar</button>
        <button type="button" @click="eliminar(cuidador.idCuidador)">
          Eliminar
        </button>
      </form>
    </fieldset>
    <router-view />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "formularioCuidadores",
  data: function () {
    return {
      cuidador: {
        idCuidador: "",
        nombre: "",
        fechaNacimiento: "",
      },
    };
  },
  methods: {
    guardar() {
      axios
        .post("http://localhost:9090/api/cuidador", this.cuidador)
        .then((data) => {
          console.log("response", data);
          this.$emit("refresh");
        });
    },

    eliminar(id) {
      axios
        .delete("http://localhost:9090/api/cuidador/" + id)
        .then((data) => {
          console.log("response", data);
          this.cuidador.idCuidador = null;
          this.$emit("refresh");
        })
        .catch(() => {
          alert("El cuidador seleccionado no existe");
        });

      console.log(id);
    },
  },
};
</script>



<style scoped>
.cuidador {
  text-align: center;
  padding: 5%;
  font-family: inherit;
}
</style>
