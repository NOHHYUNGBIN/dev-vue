<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="room.image" alt="Room Image" style="width: 100%" />
      <h4>{{ room.title }}</h4>
      <p>{{ room.content }}</p>
      <p>{{ room.price }}</p>
      <button @click="emit('update:modal', { room: {}, isOpen: false })">
        닫기
      </button>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  room: Object,
  modal: Boolean,
});
const emit = defineEmits(["update:modal"]);
</script>

<style>
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 50%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
