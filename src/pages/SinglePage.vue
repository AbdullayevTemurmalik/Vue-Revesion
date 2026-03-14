<script setup>
import { ref } from "vue";
import { Star, MapPin, Heart, Share2, Ruler, Bed, Bath } from "lucide-vue-next";

const props = defineProps(["house"]);
</script>

<template>
  <div class="single-page-wrapper" v-if="house">
    <header class="mini-header">
      <div class="container">
        <a href="/"
          ><h1 class="logo">Uy<span>Bozor</span></h1></a
        >
      </div>
    </header>

    <main class="container page-content">
      <nav class="breadcrumb">
        Bosh sahifa / Uylar / <span>{{ house.name }}</span>
      </nav>

      <div class="main-layout">
        <div class="gallery-section">
          <div class="main-img-box">
            <img :src="house.img" alt="Main house view" />
          </div>
          <div class="thumbs-row">
            <div v-for="i in 4" :key="i" class="thumb">
              <img :src="house.img" alt="thumb" />
            </div>
          </div>
        </div>

        <div class="details-section">
          <h1 class="house-title">{{ house.name }}</h1>
          <div class="rating-bar">
            <div class="stars">
              <Star
                v-for="i in 5"
                :key="i"
                size="18"
                fill="#FFAD33"
                color="#FFAD33"
              />
            </div>
            <span class="reviews">(45 ko'rildi)</span>
          </div>

          <div class="price-tag">${{ house.price }}</div>

          <p class="description">
            Bu uy barcha zamonaviy standartlarga javob beradi. Yuqori sifatli
            qurilish materiallari, keng xonalar va quyoshli tomon. Tinch mahalla
            va qulay infratuzilma.
          </p>

          <div class="house-specs">
            <div class="spec"><Ruler /> 240 m²</div>
            <div class="spec"><Bed /> 4 xona</div>
            <div class="spec"><Bath /> 2 hammom</div>
          </div>

          <div class="agent-box">
            <button class="contact-btn">Egalari bilan bog'lanish</button>
            <button class="fav-btn"><Heart /></button>
            <button class="fav-btn"><Share2 /></button>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped>
.single-page-wrapper {
  font-family: "Inter", sans-serif;
  background: #fff;
  padding-bottom: 100px;
}
.mini-header {
  padding: 20px 0;
  border-bottom: 1px solid #f0f0f0;
  margin-bottom: 30px;
}
.logo {
  font-size: 24px;
  font-weight: 700;
}
.logo span {
  color: #db4444;
}

.page-content {
  margin-top: 20px;
}
.breadcrumb {
  font-size: 14px;
  color: #7d8184;
  margin-bottom: 30px;
}
.breadcrumb span {
  color: #000;
  font-weight: 500;
}

.main-layout {
  display: flex;
  gap: 50px;
}

/* Gallery */
.gallery-section {
  flex: 1.2;
}
.main-img-box {
  width: 100%;
  height: 450px;
  background: #f5f5f5;
  border-radius: 12px;
  overflow: hidden;
}
.main-img-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.thumbs-row {
  display: flex;
  gap: 15px;
  margin-top: 15px;
}
.thumb {
  flex: 1;
  height: 100px;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
}
.thumb img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.7;
}
.thumb:hover img {
  opacity: 1;
}

/* Details */
.details-section {
  flex: 1;
}
.house-title {
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 10px;
}
.rating-bar {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 20px;
}
.reviews {
  font-size: 14px;
  color: #7d8184;
}

.price-tag {
  font-size: 28px;
  font-weight: 700;
  color: #db4444;
  margin-bottom: 20px;
}
.description {
  font-size: 15px;
  line-height: 1.7;
  color: #444;
  margin-bottom: 30px;
}

.house-specs {
  display: flex;
  gap: 20px;
  margin-bottom: 40px;
}
.spec {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 500;
  color: #000;
}

.agent-box {
  display: flex;
  gap: 15px;
}
.contact-btn {
  flex: 1;
  padding: 15px;
  background: #000;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: 0.3s;
}
.contact-btn:hover {
  background: #db4444;
}
.fav-btn {
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fff;
  cursor: pointer;
  display: flex;
  align-items: center;
}

@media (max-width: 900px) {
  .main-layout {
    flex-direction: column;
  }
}
</style>
