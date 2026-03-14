<script setup>
import { ref } from "vue";
import { Eye, Heart, Star, MapPin } from "lucide-vue-next";

const houses = ref([
  {
    id: 1,
    name: "Zamonaviy Villa",
    price: "150,000",
    rating: 5,
    img: "https://images.pexels.com/photos/1396122/pexels-photo-1396122.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Toshkent viloiyati",
  },
  {
    id: 2,
    name: "Shahar markazidagi xonadon",
    price: "85,000",
    rating: 4,
    img: "https://images.pexels.com/photos/1571460/pexels-photo-1571460.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Yunusobod",
  },
  {
    id: 3,
    name: "Luxury Penthouse",
    price: "250,000",
    rating: 5,
    img: "https://images.pexels.com/photos/323780/pexels-photo-323780.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Mirobod",
  },
  {
    id: 4,
    name: "Yashil hovli",
    price: "120,000",
    rating: 4,
    img: "https://images.pexels.com/photos/106399/pexels-photo-106399.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Namangan shahri",
  },
  {
    id: 5,
    name: "Kichik kottej",
    price: "95,000",
    rating: 5,
    img: "https://images.pexels.com/photos/1396132/pexels-photo-1396132.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Chirchiq",
  },
  {
    id: 6,
    name: "Dream Home",
    price: "300,000",
    rating: 5,
    img: "https://images.pexels.com/photos/101808/pexels-photo-101808.jpeg?auto=compress&cs=tinysrgb&w=500",
    loc: "Samarqand",
  },
]);
</script>

<template>
  <div class="home-container">
    <header class="site-header">
      <div class="container nav-wrap">
        <a href="/"
          ><h1 class="logo">Uy<span>Bozor</span></h1></a
        >
        <nav class="main-nav">
          <a href="#">Bosh sahifa</a>
          <a href="#">Uylar</a>
          <a href="#">Aloqa</a>
        </nav>
      </div>
    </header>

    <main class="container main-content">
      <h2 class="title">Saralangan takliflar</h2>
      <div class="grid">
        <div v-for="house in houses" :key="house.id" class="house-card">
          <div class="image-box">
            <img :src="house.img" alt="house" />
            <div class="overlay-icons">
              <button class="icon-btn like"><Heart size="18" /></button>
              <button class="icon-btn eye" @click="$emit('view-single', house)">
                <Eye size="18" />
              </button>
            </div>
          </div>
          <div class="info">
            <h3>{{ house.name }}</h3>
            <p class="loc"><MapPin size="14" /> {{ house.loc }}</p>
            <div class="price-row">
              <span class="price">${{ house.price }}</span>
              <div class="stars">
                <Star
                  v-for="i in 5"
                  :key="i"
                  size="14"
                  :fill="i <= house.rating ? '#FFAD33' : 'none'"
                  color="#FFAD33"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>

    <footer class="site-footer">
      <div class="container footer-content">
        <p>&copy; 2026 UyBozor platformasi. Barcha huquqlar himoyalangan.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
.home-container {
  font-family: "Inter", sans-serif;
  background: #fff;
}
.container {
  max-width: 1170px;
  margin: 0 auto;
  padding: 0 15px;
}

/* Header */
.site-header {
  padding: 20px 0;
  border-bottom: 1px solid #f0f0f0;
  background: #fff;
  position: sticky;
  top: 0;
  z-index: 100;
}
.nav-wrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo {
  font-size: 24px;
  font-weight: 700;
  color: #000;
}
.logo span {
  color: #db4444;
}
.main-nav {
  display: flex;
  gap: 30px;
}
.main-nav a {
  text-decoration: none;
  color: #000;
  font-weight: 500;
  font-size: 14px;
}

/* Content */
.main-content {
  padding: 40px 0 80px;
}
.title {
  font-size: 24px;
  margin-bottom: 30px;
  font-weight: 600;
  color: #000;
  border-left: 5px solid #db4444;
  padding-left: 15px;
}
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

/* Card */
.image-box {
  position: relative;
  background: #f5f5f5;
  border-radius: 8px;
  overflow: hidden;
  height: 260px;
}
.image-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: 0.5s;
}
.house-card:hover img {
  transform: scale(1.05);
}
.overlay-icons {
  position: absolute;
  top: 12px;
  right: 12px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.icon-btn {
  background: #fff;
  border: none;
  width: 36px;
  height: 36px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.info {
  padding: 15px 0;
}
.info h3 {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 5px;
  color: #000;
}
.loc {
  display: flex;
  align-items: center;
  gap: 5px;
  font-size: 13px;
  color: #7d8184;
  margin-bottom: 10px;
}
.price-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.price {
  color: #db4444;
  font-size: 18px;
  font-weight: 700;
}

/* Footer */
.site-footer {
  padding: 40px 0;
  background: #000;
  color: #fff;
  text-align: center;
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
@media (max-width: 600px) {
  .grid {
    grid-template-columns: 1fr;
  }
  .main-nav {
    display: none;
  }
}
</style>
