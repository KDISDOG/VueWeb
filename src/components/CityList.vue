<template>
  <div></div>
</template>

<script setup>
import axios from "axios";
import { ref } from "vue";

const savedCities = ref([]);
const getCities = () => {
  if (localStorage.getItem("savedCities")) {
    savedCities.value = JSON.parse(localStorage.getItem("savedCities"));
  }
  const requests = [];
  savedCities.value.forEach((city) => {
    requests.push(
      axios.get(
        `https://api.openweathermap.org/data/2.5/weather?lat=${city.coords.lat}&lon=${city.coords.lng}&appid=7efa332cf48aeb9d2d391a51027f1a71&units=imperial`
      )
    );
  });
};
</script>
