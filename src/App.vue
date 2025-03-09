<script setup>
import { ref, watch } from "vue";
import data from "./assets/roomData";
import Discount from "./components/Discount.vue";
import Card from "./components/Card.vue";

const menus = ref(["Home", "Shop", "About"]);
const rooms = ref(data);
const modal = ref(false);
const selected = ref(0);
</script>

<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="rooms[selected].image" alt="Room Image" style="width: 100%" />
      <h4>{{ rooms[selected].title }}</h4>
      <p>{{ rooms[selected].content }}</p>
      <p>{{ rooms[selected].price }}</p>
      <button @click="modal = !modal">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Discount :menus="menus" />
  <Card v-for="room in rooms" :key="room.id" :room="room" />

  <!-- <div v-for="(room, i) in rooms" :key="room">
    <div>
      <img
        :src="room.image"
        @click="
          modal = !modal;
          selected = i;
        "
        alt="Room Image"
        class="room-img"
      />
      <h4>{{ room.title }}</h4>
      <p>{{ room.price }}원</p>
    </div>
  </div> -->
</template>

<style scoped>
.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
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
  width: 50%;
  margin-top: 40px;
  display: block;
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
