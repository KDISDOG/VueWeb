<template>
  <header class="sticky top-0 bg-weather-primary shadow-lg">
    <nav
      class="container flex flex-row items-center gap-4 text-white py-6 sm:text-sm"
    >
      <RouterLink :to="{ name: 'home' }">
        <div class="flex items-center gap-3 flex-1">
          <i class="fa-solid fa-sun md:text-2xl"></i>
          <p class="md:text-2xl">The Local Weather</p>
        </div>
      </RouterLink>
      <div class="flex gap-3 flex-1 justify-end">
        <i
          @click="toggleModal"
          class="fa-solid fa-circle-info md:text-xl hover:text-weather-secondary duration-150 cursor-pointer"
        ></i>
        <i
          class="fa-solid fa-plus md:text-xl hover:text-weather-secondary duration-150 cursor-pointer"
          @click="addCity"
        ></i>
      </div>
      <BaseModal :modalActive="modalActive" @closeButton="toggleModal">
        <li>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Enim soluta
          alias quia magnam, aliquid
        </li>

        <li>
          aspernatur odit est adipisci porro fugiat quasi a totam cumque hic,
          corporis aliquam ratione labore. Odit!
        </li>
      </BaseModal>
    </nav>
  </header>
</template>

<script setup>
import { RouterLink } from "vue-router";
import BaseModal from "../components/BaseModal.vue";
import { ref } from "vue";
import { uid } from "uid";
const modalActive = ref(null);
const saveCities = ref([]);

const toggleModal = () => {
  modalActive.value = !modalActive.value;
};

const addCity = () => {
  if(localStorage.getItem("saveCities")){
    saveCities.value=JSON.parse(
      localStorage.getItem("saveCities")
    );
  }
}

const localtionObj ={
  id:uid(),
}
</script>
