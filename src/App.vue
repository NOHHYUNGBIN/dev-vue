<script setup>
import { ref } from "vue";

const menus = ref(["역삼동원룸", "천호동원룸", "봉천동원룸"]);
const count = ref(0)
const info = ref([{
  id:'shgudqlsz',
  name: '노형빈'
}])
const test = (props) => {
  console.debug(props)
  info.value.push({id:'ㅋㅋ', name:'이상경'})
}
</script>

<template>
  <div v-for="menu in menus" :key="menu">
    <a>{{ menu }}</a>
    <button @click="test('안녕녕')">허위매물신고</button><span>신고수 : {{count}}</span>
  </div>
  <div v-for="data in info" :key="data.id">
    <p>
      {{ data.id }}
    </p>
    <p>
      {{ data.name }}
    </p>
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
