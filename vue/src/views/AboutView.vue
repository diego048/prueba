<template>
  <div class="register">
    <h2>Registrate</h2>
    <input type="text" v-model="correo" placeholder="E-mail" />
    <input type="text" v-model="nombre" placeholder="Username" />
    <input type="text" v-model="texto" placeholder="Username" />
    <a v-on:click="signUp" href="#"><button>Sign Up</button></a>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "AboutView",
  data() {
    return {
      correo: "",
      nombre: "",
      texto: "",
    };
  },
  methods: {
    async signUp() {
      let result = await axios.post("http://54.205.29.249:5000/correo", {
        correo: this.correo,
        nombre: this.nombre,
        texto: this.texto,
      });
      console.warn(result);
      if (result.data.success == true) {
        localStorage.setItem("user-info", JSON.stringify(result.data.user));
        this.$router.push("/VerPost");
        location.reload();
      }
    },
  },
};
</script>
