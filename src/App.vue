<script setup>
import {ref} from 'vue'
import Gallery from './components/Gallery.vue'
import TextContent from './components/TextContent.vue'

const photos = ref([
  { id: 1, title: "Coucher de soleil", url: "https://picsum.photos/300/200?random=1" },
  { id: 2, title: "Montagne enneigée", url: "https://picsum.photos/300/200?random=2" },
  { id: 3, title: "Forêt mystérieuse", url: "https://picsum.photos/300/200?random=3" },
  { id: 4, title: "Ville de nuit", url: "https://picsum.photos/300/200?random=4" },
  { id: 5, title: "Plage paradisiaque", url: "https://picsum.photos/300/200?random=5" },
  { id: 6, title: "Désert infini", url: "https://picsum.photos/300/200?random=6" }
])

const currentIndex = ref(0)


</script>

<template>
  <section  >
    <header>
      <h1>My Photos Gallery</h1>
    </header>
    <TextContent :photos="photos" :currentIndex="currentIndex" />
    <Gallery :photos="photos" v-model:currentIndex="currentIndex" />



  </section>
</template>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90px;
  /* border: 1px solid black; */

}
h1{
  font-family: "Bungee", sans-serif;
  font-size: 100px;
  color: #d75150;
  justify-content: center;
  align-items: center;

}


</style>
