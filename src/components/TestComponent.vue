<template>
  <div class="test-class" :style="{ background: color }">test component</div>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      default: "tomato",
    },
  },
  data() {
    return {};
  },
};
</script>

<style>
.test-class {
  width: 100%;
  height: 100vh;
  border: 2px solid salmon;
}
</style>
