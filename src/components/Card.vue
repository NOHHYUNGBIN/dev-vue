<template>
  <div>
    <img :src="room.image" alt="Room Image" class="room-img" />
    <h4>{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
  </div>
</template>

<script setup>
const props = defineProps({
  room: Object,
});
</script>

<style></style>
