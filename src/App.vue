<script setup>
import { ref } from "vue";

const menus = ref(["역삼동원룸", "천호동원룸", "봉천동원룸"]);
</script>

<template>
  <div v-for="menu in menus" :key="menu">
    <a>{{ menu }}</a>
  </div>
</template>

<style scoped>
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
