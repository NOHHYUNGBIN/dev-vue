<script setup>
import { ref, watch } from "vue";
import data from "./assets/roomData";
import Discount from "./components/Discount.vue";
import Card from "./components/Card.vue";
import Modal from "./components/Modal.vue";

const menus = ref(["Home", "Shop", "About"]);
const originRooms = ref([...data]);
const rooms = ref(data);
const modal = ref(false);
const selectedRoom = ref({});

const openModalHandler = (data) => {
  selectedRoom.value = data?.room;
  modal.value = data.isOpen;
};
const priceSort = () => {
  rooms.value.sort((a, b) => a.price - b.price);
};
const backSort = () => {
  console.debug("originRooms.value", originRooms.value);
  rooms.value = [...originRooms.value];
};
</script>

<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <Modal :room="selectedRoom" :modal="modal" @update:modal="openModalHandler" />

  <Discount :menus="menus" />

  <button @click="priceSort">가격순 정렬</button>
  <button @click="backSort">되돌리기</button>

  <Card
    v-for="(room, i) in rooms"
    :key="room.id"
    :room="room"
    :modal="modal"
    @update:modal="openModalHandler"
  />
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
</style>
