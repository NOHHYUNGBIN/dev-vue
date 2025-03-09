<template>
  <div class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="room.image" alt="Room Image" style="width: 100%" />
      <h4>{{ room.title }}</h4>
      <p>{{ room.content }}</p>
      <input
        ref="inputRef"
        v-input="month"
        placeholder="개월 수 입력(최대24개월)"
        @input="debouncedValidateMonth"
      />
      <p>
        {{ month ? month : 1 }}개월
        {{ month ? room.price * month : room.price }}
      </p>
      <button @click="emit('update:modal', { room: {}, isOpen: false })">
        닫기
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";
const month = ref(null);
const inputRef = ref(null);
const props = defineProps({
  room: Object,
  modal: Boolean,
});
const emit = defineEmits(["update:modal"]);

let debounceTimer = null;

const validateMonth = (e) => {
  let value = e.target.value;

  if (isNaN(value)) {
    inputRef.value.value = null;
    alert("숫자만 입력 가능합니다.");
    return;
  }
  if (value > 24 || value < 1) {
    inputRef.value.value = null;
    alert("1개월이상 24개월 이하만 입력 가능합니다.");
    return;
  }
  month.value = value;
};
const debouncedValidateMonth = (e) => {
  clearTimeout(debounceTimer); // 기존 타이머 삭제
  debounceTimer = setTimeout(() => {
    validateMonth(e); // 500ms 후 실행
  }, 500);
};
watch(month, (newVal) => {
  console.debug("newValnewVal", newVal);
});
// watch(month, (newVal, oldVal) => {
//   clearTimeout(debounce);
//   debounce = setTimeout(() => {
//     if (isNaN(newVal)) {
//       alert("숫자만 입력 가능합니다.");
//       month.value = 1;
//       return;
//     }
//     if (newVal > 24 || newVal < 1) {
//       alert("1개월이상 24개월 이하만 입력 가능합니다.");
//       month.value = 1;
//       return;
//     }
//   }, 500);
// });
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
