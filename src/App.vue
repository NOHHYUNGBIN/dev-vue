<script setup>
import { ref } from "vue";

const menus = ref(["Home", "Shop", "About"]);
const rooms = ref(["역삼동원룸", "대치동원룸", "봉천동원룸"]);
const count = ref(0);
const modal = ref(false);
</script>

<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="modal = !modal">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <div v-for="(room, idx) in rooms" :key="room" class="room-img">
    <div @click="modal = !modal">
      <img src="./assets/room0.jpg" alt="Room Image" />
      <h4>{{ room }}</h4>
    </div>
    <button @click="count++">허위매물신고</button>
    <span>신고수 : {{ count }}</span>
  </div>
</template>

<style scoped>
.menu {
  background-color: darkcyan;
  padding: 15px;
  border-radius: 15px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
