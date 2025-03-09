<template>
  <div>
    <img
      @click="emit('update:modal', { room, isOpen: true })"
      :src="room.image"
      alt="Room Image"
      class="room-img"
    />
    <h4>{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
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
.room-img {
  width: 50%;
  margin-top: 40px;
  display: block;
}
</style>
