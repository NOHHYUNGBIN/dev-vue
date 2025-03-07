<template>
  <div class="discont">
    <h4>지금 결제하면 20% 할인</h4>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  menus: Array,
});
console.debug("props", props);
</script>
<style></style>
