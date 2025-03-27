<template>
  <div class="menu">
    <a v-for="i in menus" :key="i" class="menu-item">{{ i }}</a>
  </div>

  <div v-for="(room, index) in oneroom" :key="room.id" class="room-card">
    <div class="black-bg" v-if="modal === index">
      <div class="white-bg">
        <img :src="room.image" class="room-img" />
        <h4 @click="modal = index">{{ room.title }}</h4>
        <p :style="스타일">{{ room.price }}만원대</p>
        <button @click="modal = false" class="close-btn">닫기</button>
      </div>
    </div>

    <img :src="room.image" class="room-img" />
    <h4 @click="modal = index">{{ room.title }}</h4>
    <p :style="스타일">{{ room.price }}만원대</p>
    <button @click="신고수[index] += 1" class="report-btn">허위매물신고</button>
    <span class="report-count">신고수: {{ 신고수[index] }}</span>
  </div>
</template>

<script>
import data from "./assets/oneroom";

export default {
  name: "App",
  data() {
    return {
      oneroom: data,
      menus: ["Home", "Shop", "About"],
      신고수: [0, 0, 0, 0, 0, 0],
      스타일: "color:blue",
      modal: null,
    };
  },
  methods: {
    increase(index) {
      this.신고수[index] += 1;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: "Arial", sans-serif;
  background-color: #f4f4f9;
}

div {
  box-sizing: border-box;
}

.menu {
  display: flex;
  justify-content: center;
  background-color: #2c3e50;
  padding: 20px 0;
}

.menu-item {
  color: white;
  font-size: 18px;
  margin: 0 20px;
  text-decoration: none;
  transition: color 0.3s;
}

.menu-item:hover {
  color: #3498db;
}

.room-card {
  background-color: white;
  margin: 20px auto;
  width: 80%;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease;
}

.room-card:hover {
  transform: scale(1.05);
}

.room-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-bottom: 2px solid #f0f0f0;
  border-radius: 10px 10px 0 0;
}

h4 {
  font-size: 22px;
  color: #333;
  padding: 10px;
  cursor: pointer;
  transition: color 0.3s ease;
}

h4:hover {
  color: #3498db;
}

p {
  font-size: 18px;
  color: #777;
  padding: 0 20px;
}

.report-btn {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.report-btn:hover {
  background-color: #c0392b;
}

.report-count {
  display: block;
  text-align: center;
  margin-top: 10px;
  color: #333;
  font-size: 16px;
}

.black-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
}

.white-bg {
  background: white;
  padding: 20px;
  border-radius: 8px;
  width: 80%;
  max-width: 500px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.close-btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 10px;
  transition: background-color 0.3s ease;
}

.close-btn:hover {
  background-color: #2980b9;
}
</style>
