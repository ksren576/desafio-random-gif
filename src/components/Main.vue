<template>
  <div>
    <div class="container">
      <h1 class="text-center">Ramdom Gif Cat</h1>
    </div>
    <Formulario />
  </div>
</template>

<script>
import Formulario from './Formulario';

export default {
  name: "Main",
  data() {
    return {
      nombre: "",
      response: null,
    };
  },
  components: {
    Formulario
  },
  methods: {
    async getData() {
      try {
        const url = `https://cataas.com/cat/gif/says/holi?filter=sepia&color=orange&size=40&type=or`;
        const req = await fetch(url);
        const reqJSON = await req.json();
        this.response = reqJSON;
        console.log(reqJSON);
      } catch (error) {
        console.log(error);
      }
    },
  },
  computed: {
    name() {
      return this.data;
    },
  },
};
</script>


<style scoped>
h1 {
    margin: 50px;
}
</style>