<script setup>
import { ref,computed} from 'vue'

const props = defineProps({
  photos:{
    type: Array,
  },
  currentIndex: {
    type : Number,
  }

})



const visibleTitles = computed (() => {
  const result = []
  for (let i = 0 ; i < 3 ; i++) {
    const photo = props.photos[(props.currentIndex + i ) % props.photos.length]
    if (photo) result.push(photo.title)
  }
  return result
})
</script>

<template>

    <h3>  </h3>

    <div class="textContent" >
      <p v-for="(title, index ) in visibleTitles" :key="index">{{ title }}</p>
      <!-- <p v-for="(title, index) in visibleTitles" :key="index">{{ title }}</p> -->


    </div>
</template>

<style scopted>

h3{
  margin: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.textContent {
  display: flex;
  justify-content: center;
  align-items: center;
  /* gap: 10px; */
  margin-top: 20px;
  flex-wrap: nowrap;
}

.textContent p {
  width: 500px;
  align-items: center;

  text-align: center;
  font-weight: bold;
  color: #d75150;
  overflow: hidden;
  white-space: nowrap;
}
</style >

