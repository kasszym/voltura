<script setup>
const emit = defineEmits(["handleClick"]);
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  backgroundColor: {
    type: String,
    default: "var(--main-color)",
  },
  color: {
    type: String,
    default: "#FFFFFF",
  },
  width: {
    type: String,
    default: "195px",
  },
  height: {
    type: String,
    default: "44px",
  },
  fontSize: {
    type: String,
    default: "var(--fs-xs)",
  },
});
</script>
<template>
  <el-button
    class="button-component"
    :style="{
      background: backgroundColor,
      color: color,
      width: width,
      height: height,
      fontSize: fontSize,
    }"
    @click="emit('handleClick')"
    >{{ title }}</el-button
  >
</template>
<style scoped>
.button-component {
  border: none;
  border-radius: 12px;
  font-weight: 700;
}
</style>
