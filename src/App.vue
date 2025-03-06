<script setup>
import { ref, watch } from "vue";
import data from "./assets/roomData";

const menus = ref(["Home", "Shop", "About"]);
const rooms = ref(data);
const modal = ref(false);

const selected = ref(0);

console.debug("selected", selected.value);
watch(selected, (newVal, oldVal) => {
  console.debug("newVal", newVal, "oldVal", oldVal);
  console.debug(newVal);
});
</script>

<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>{{ rooms[selected].title }}</h4>
      <p>상세페이지 내용</p>
      <button @click="modal = !modal">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <div v-for="(room, i) in rooms" :key="room">
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
