<template>
  <div class="discont">
    <h4>지금 결제하면 20% 할인</h4>
  </div>
</template>

<script>
export default {
  name: "Discount",
  props: {
    menus: Array,
  },
  mounted() {
    console.debug("props", this.menus);
  },
};
</script>
<style></style>
