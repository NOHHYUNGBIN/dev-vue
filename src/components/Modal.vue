<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="room.image" alt="Room Image" style="width: 100%" />
      <h4>{{ room.title }}</h4>
      <p>{{ room.content }}</p>
      <input v-model="month" />
      <p>{{ month }}개월 {{ room.price * month }}</p>
      <button @click="emit('update:modal', { room: {}, isOpen: false })">
        닫기
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";
const month = ref(1);
const props = defineProps({
  room: Object,
  modal: Boolean,
});
const emit = defineEmits(["update:modal"]);

let debounce = null;

watch(month, (newVal, oldVal) => {
  clearTimeout(debounce);
  debounce = setTimeout(() => {
    if (isNaN(newVal)) {
      alert("숫자만 입력 가능합니다.");
      month.value = 1;
      return;
    }
    if (newVal > 24 || newVal < 1) {
      alert("1개월이상 24개월 이하만 입력 가능합니다.");
      month.value = 1;
      return;
    }
  }, 500);
});
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
