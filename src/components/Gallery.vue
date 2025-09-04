<script setup>
import { faMinus, faPlus } from '@fortawesome/free-solid-svg-icons'
import {ref , computed} from 'vue'

const props = defineProps({
  photos:{
    type: Array,
  }
})
const addPicture = (photos) => {
  photos.push(add)
}
const add = ref({ "id": 999, "title": "Nouvelle photo ajoutée", "url": "https://picsum.photos/300/200?random=99" })

const currentIndex = ref(0)

const visiblePhotos = computed (() =>{
  const result = []
  for (let i = 0 ; i < 3; i++) {
    const photo = props.photos[(currentIndex.value + i ) % props.photos.length]
    if (photo) result.push(photo)
  }
  return result
})

const nextPhoto = () => {
  currentIndex.value = (currentIndex.value+1) % props.photos.length
}

const previousPhoto = () => {
  currentIndex.value = (currentIndex.value - 1 + props.photos.length) % props.photos.length
}


</script>

<template>
  <!-- <section class="buttonAddPicture">
    <button @click="addPicture(photos)">Ajouter une photo</button>
  </section> -->

  <section class="gallery">
    <button class="previousPhoto" @click = "previousPhoto()">
      <font-awesome-icon :icon="faMinus" />
    </button>
    <div class=imgContenair v-for="photo in visiblePhotos" :key="photo.id">
      <div class="card">
        <img :src="photo.url" :alt="photo.title"/>
      </div>
    </div>
    <button class="nextPhoto" @click = "nextPhoto()">
      <font-awesome-icon :icon="faPlus" />

    </button>

  </section>


</template>

<style scopted>

.gallery{
  height: calc(100vh-280px-90px);
  /* border: 1px solid black; */
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 10px;

}

.minus{
color: rgb(154, 12, 12);
}
.buttonAddPicture {
  all: unset;
  height: 30px;
  width: 200px;
  border-radius: 20px;
  background-color: black;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
}
.imgContenair{
  /* flex-direction: row; */
  /* flex-wrap: wrap; */
  height: 550px;
  width: 500px;
  /* gap: 50px; */
}


.card{
  border: 10px solid #d75150;
  height: 100%;
  width: 100%;
}

img{
  height: 100%;
  width: 100%;
  object-fit: cover;
  /* object-position: 50% 50%; */

}

</style>