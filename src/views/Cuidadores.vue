<template>
  <div class="cuidador">
    <formularioCuidadores @refresh="refrescar" />
    <tablaCuidadores :cuidadores="cuidadores" />
  </div>
</template>

<script>
import formularioCuidadores from "@/components/formularioCuidadores.vue";
import tablaCuidadores from "@/components/tablaCuidadores.vue";
import axios from "axios";

export default {
  name: "Cuidadores-view",
  components: {
    formularioCuidadores,
    tablaCuidadores,
  },
  data: () => ({
    cuidadores: [],
  }),
  mounted() {
    this.getCuidadores();
  },
  methods: {
    refrescar() {
      this.getCuidadores();
    },
    getCuidadores() {
      axios
        .get("http://localhost:9090/api/cuidador/listar")
        .then((response) => {
          this.cuidadores = response.data;
        });
    },
  },
};
</script>

<style scoped>
.cuidador {
  text-align: center;
}
</style>