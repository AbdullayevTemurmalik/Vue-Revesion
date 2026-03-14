<script setup>
import { ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import SinglePage from "./pages/SinglePage.vue";

// Tanlangan uyni saqlash uchun holat
const selectedHouse = ref(null);

// Uyni tanlaganda ishlaydigan funksiya
const openSinglePage = (house) => {
  selectedHouse.value = house;
  window.scrollTo(0, 0); // Sahifani tepaga qaytarish
};

// Orqaga (Bosh sahifaga) qaytish
const goBack = () => {
  selectedHouse.value = null;
};
</script>

<template>
  <div class="app-main">
    <div v-if="!selectedHouse">
      <HelloWorld @view-single="openSinglePage" />
    </div>

    <div v-else>
      <div class="container nav-back">
        <button class="back-btn" @click="goBack">
          ← Bosh sahifaga qaytish
        </button>
      </div>
      <SinglePage :house="selectedHouse" />
    </div>
  </div>
</template>

<style>
/* Global yoki App darajasidagi minimal stillar */
.app-main {
  min-height: 100vh;
  background-color: #fff;
}

.container {
  max-width: 1170px;
  margin: 0 auto;
  padding: 0 15px;
}

.nav-back {
  padding-top: 20px;
}

.back-btn {
  background: #db4444;
  color: #fff;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: 500;
  transition: 0.3s;
}

.back-btn:hover {
  background: #000;
}
</style>
