<script setup>
import { ref,computed } from 'vue';

const styleRed = "color: red;";

const styleGreen = "color: green;";


const total = ref(0)
const fav = ref([])

const classTotal = computed(()=>{
  if (total.value <= 0){
    return 'red'
  }else{
    return 'green'
  }
})


const disableButton = computed(()=>{
  if(fav.value.find(item => item === total.value.toString())){
    return true
  }else{
    return false
  }
})

const handleSumar = () => {
  total.value++
}


const handleRestar = () => {
  total.value--
}

const handleFavorios = () => {

    fav.value.push(total.value.toString())

}

</script>



<template>
  <button @click="handleSumar">
    Sumar
  </button>
  <button @click="handleRestar">
    Restar
  </button>
  <button @click="handleFavorios" :disabled="disableButton">
    Agregar a Favoritos
  </button>
  <p :class="classTotal">Total {{ total }}</p>

  <template v-for="numero in fav">
    <p>{{ numero }}</p>
  </template>
  
</template>


<style>
.green {
  background-color: green;
}

.red{
  background-color: red;
}

</style>


