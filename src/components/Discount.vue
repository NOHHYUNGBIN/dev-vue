<template>
  <div class="discont">
    <h4>지금 결제하면 20% 할인</h4>
  </div>
</template>

<script setup>
import { defineProps, onMounted } from "vue";

const props = defineProps({
  menus: Array,
});

onMounted(() => {
  console.debug("props", props.menus);
});
</script>

<style></style>
