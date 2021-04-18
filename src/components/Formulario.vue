<template>
  <div>
    <div class="formulario">
      <div class="container">
        <div class="mb-3 row">
          <label class="col-sm-2 col-form-label">Título</label>
          <div class="col-sm-10">
            <input type="text" v-model="titulo" class="form-control" />
          </div>
        </div>
        <div class="mb-3 row">
          <label class="col-sm-2 col-form-label">Filtro</label>
          <div class="col-sm-10">
            <select class="form-select" v-model="filtro">
              <option value="blur">Blur</option>
              <option value="mono">Mono</option>
              <option value="sepia">Sepia</option>
              <option value="negative">Negative</option>
              <option value="paint">Paint</option>
              <option value="pixel">Pixel</option>
            </select>
          </div>
        </div>
        <div class="mb-3 row">
          <label class="col-sm-2 col-form-label">Color</label>
          <div class="col-sm-9">
            <select
              class="form-select"
              v-model="color"
              aria-label="Default select example"
            >
              <option value="green">Verde</option>
              <option value="blue">Azul</option>
              <option value="orange">Naranjo</option>
              <option value="red">Rojo</option>
              <option value="white">Blanco</option>
            </select>
          </div>
          <div class="col-sm-1">
            <div :class="estiloCirculo"></div>
          </div>
        </div>
        <div class="mb-3 row">
          <label class="col-sm-2 col-form-label">Tamaño</label>
          <div class="col-sm-10">
            <input type="text" v-model="tamano" class="form-control" />
          </div>
        </div>
      </div>
    </div>
    <br />
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-auto">
          <button @click="obtenerImagen()" class="btn btn-light">
            Obtener mi gatito
          </button>
          <br />
          <br />
          <img v-if="url" :src="url" alt="gatito" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      color: "green",
      url: "",
      tamano: "",
      filtro: "blur",
      titulo: "",
    };
  },
  methods: {
    obtenerImagen() {
      let mensaje = "";
      if (!this.titulo || !this.tamano) {
        mensaje += "- Complete los campos del formulario\n";
      }

      if (Number.isNaN(Number(this.tamano))) {
        mensaje += "- El campo tamaño debe ser un número entero";
        this.tamano = "";
      }

      if (mensaje) {
        alert(mensaje);
      } else {
        this.url = `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamano}`;
      }
    },
  },
  computed: {
    estiloCirculo() {
      return {
        "color-circle": true,
        "rounded-circle": true,
        "border border-secondary": true,
        "circulo-verde": this.color === "green",
        "circulo-azul": this.color === "blue",
        "circulo-naranjo": this.color === "orange",
        "circulo-rojo": this.color === "red",
        "circulo-blanco": this.color === "white",
      };
    },
  },
};
</script>

<style scoped>
.color-circle {
  height: 100%;
  width: 40px;
}

.circulo-verde {
  background-color: green;
}
.circulo-azul {
  background-color: blue;
}
.circulo-naranjo {
  background-color: orange;
}
.circulo-rojo {
  background-color: red;
}
.circulo-blanco {
  background-color: white;
}

.formulario {
  background-color: salmon;
  padding: 30px 0;
}
</style>