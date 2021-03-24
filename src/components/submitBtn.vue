<template>
  <button :style="{ background: bgColor, color: textColor, border: border }">
    {{ text }}
  </button>
</template>

<style scoped>
button {
  display: block;
  margin: 2rem auto;
}
</style>

<script>
export default {
  name: "submitBtn",
  props: {
    text: String,
    bgColor: String,
    textColor: String,
    border: String,
  },
};
</script>
