<template>
  <div class="container">
    <h1 class="title">Álbums de la página:</h1>
    <div class="columns is-multiline">
      <album-card :album="album" v-for="album in albums" :key="album.id"/>
    </div>
    <a href="https://stories.devacademy.la/6-pasarelas-de-pago-que-debes-conocer-d5ae78f9369c">Pasarelas de pago</a>
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
  created() {
    axios.get(`${env.endpoint}/albums`)
      .then(res => {
        this.albums = res.data
      })
  }
}
</script>

<style scoped>

</style>