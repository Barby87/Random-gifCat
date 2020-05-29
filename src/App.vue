<template>
  <div id="app">
    <section class="light-blue py-5">
      <h1 class="font-weight-bold">{{title}}</h1>
    </section>

    <section class="red">
      <form class="container p-5">
        <div class="form-group"><label>Título:</label>
          <input type="text" class="form-control" v-model="titulo">
        </div>
        <div class="form-group">
          <label>Filtro:</label>
          <select class="form-control" v-model="filtro">
            <option value="blur">Blur</option>
            <option value="mono">Mono</option>
            <option value="negative">Negative</option>
            <option value="paint">Paint</option>
            <option value="pixel">Pixel</option>
            <option value="sepia">Sepia</option>
          </select>
        </div>
        <div class="form-group">
          <label>Color:</label>
          <select class="form-control" v-model="color">
            <option value="yellow">Amarillo</option>
            <option value="blue">Azúl</option>
            <option value="purple">Morado</option>
            <option value="orange">Naranjo</option>
            <option value="red">Rojo</option>
            <option value="green">Verde</option>
          </select>
        </div>
        <div class="form-group">
          <label>Tamaño:</label>
          <input type="text" class="form-control" v-model="tamano" @keyup.enter="showImage">
        </div>
        <button type="button" class="btn btn-success" @click="showImage">Obtener mi gatito</button>
      </form>
    </section>

    <section class="light-blue py-5" id="image">
      <div class="mb-5">
        <img :src="urlImage" alt="">
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      title: 'Random Gif Cat',
      urlImage: null,
      titulo: null,
      color: null,
      filtro: null,
      tamano: null
    }
  },
  methods: {
    showImage() {
      this.urlImage = `https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamano}`;
      console.log('url', this.urlImage);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.light-blue {
  background-color: #c3edea;
}

.image {
  height: 1000px;
}

.red {
  background-color: #ff847c;
}
</style>
