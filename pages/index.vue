<template>
  <div class="container">
    <header>
      <h1 class="title">Álbums de la página:</h1>
    </header>
    <div class="columns is-multiline">
      <album-card :album="album" v-for="album in albums" :key="album.id"/>
    </div>
    <a href="https://www.youtube.com/watch?v=DwMBu34rIOw" target="_blank" class="button is-primary">Continuar Curso</a>
    <br><br>
    <a href="https://stories.devacademy.la/6-pasarelas-de-pago-que-debes-conocer-d5ae78f9369c" class="button is-primary">Pasarelas de pago</a>
  </div>
</template>

<script>
import axios from 'axios';
import env from '../config/env';
import AlbumCard from '../components/AlbumCard'
export default {
  components: {
    AlbumCard
  },
  data() {
    return {
      albums: []
    }
  },
  created: async function() {
    let albumsRes = await axios.get(`${env.endpoint}/albums`);
    this.albums = albumsRes.data;
    // axios.get(`${env.endpoint}/albums`)
    //   .then(res => {
    //     this.albums = res.data
    //   })
  }
}
</script>

<style scoped>

</style>