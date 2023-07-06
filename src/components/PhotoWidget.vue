<template>
  <div class="photo-widget">
      <h1 class="ket1">Pintasan Foto</h1>
    <div class="image-container">
      <img :src="currentPhoto" :alt="currentPhoto" :style="{ width: '1000px', height: 'auto' }" />
    </div>
    <div class="controls-foto">
      <button class="button-tertiary" @click="kembaliKeBeranda">Kembali ke Beranda</button>
      <button class="button-tertiary" @click="prevPhoto">Sebelumnya</button>
      <button class="button-tertiary" @click="nextPhoto">Selanjutnya</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      photos: [require('../assets/jettt.jpg'),require('../assets/neon.jpg'),require('../assets/pestavalorant.jpg'),require('../assets/pionixjett.jpg'),require('../assets/raze.jpg'),require('../assets/raze2.jpeg'),require('../assets/razee.jpg'),require('../assets/reyna.jpg'),require('../assets/valorant.jpg'),require('../assets/valorant1.jpg'),require('../assets/valorant2.jpg'),require('../assets/valorant3.jpg'),require('../assets/viper.jpg'),require('../assets/viper1.jpg'),require('../assets/viper1.png'),require('../assets/jett1.jpg')],
      currentIndex: 0,
    };
  },
  computed: {
    currentPhoto() {
      return this.photos[this.currentIndex];
    },
  },
  methods: {
    kembaliKeBeranda() {
      this.$router.push('/cuaca')
    },
    prevPhoto() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      } else {
        this.currentIndex = this.photos.length - 1;
      }
    },
    nextPhoto() {
      if (this.currentIndex < this.photos.length - 1) {
        this.currentIndex++;
      } else {
        this.currentIndex = 0;
      }
    },
  },
};
</script>

<style scoped>
.ket1 {
  font-weight: bold;
  margin-top: 1px;
  margin-bottom: 12px;
  color: rgb(197, 31, 31);
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  text-shadow: 2px 2px 4px rgba(243, 238, 238, 0.5);
  font-style: italic;
  padding: 10px 66px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.6);
  color: rgb(255, 255, 255);
  border-top-left-radius: 66px;
  border-bottom-right-radius: 66px;
}

.photo-widget {
  margin: 1px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: rgb(146, 146, 146);
  border-top-right-radius: 40px;
  border-bottom-left-radius: 40px;
  padding: 22px;
  
}

.image-container {
  margin-bottom: 20px;
  border: 3px solid rgb(71, 207, 8); 
  padding: 5px;
  display: flex;
  justify-content: center;
  border-radius: 4px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 5px 15px rgba(0, 0, 0, 0.1), 0 10px 30px rgba(0, 0, 0, 0.1);
}
.image-container img {
  max-width: 100%;
  max-height: 100%;
  border-radius: 4px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.7);
  
}

.controls-foto {
  display: flex;
  justify-content: center;
  margin-top: 20px;
 
}

.controls-foto button {
  padding: 10px 20px;
  margin: 4px 9px;
  font-size: 16px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  background-color: #2196f3;
  color: white;
}

.controls-foto button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.controls-foto button:active {
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>
