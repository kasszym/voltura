<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  images: {
    type: Array,
    required: true,
  },
});

const i = ref(0)
const current = computed(() => props.images[i.value] || null);

const select = (idx) => (i.value = idx);
const next = () => {
  if (i.value !== filteredImages.value.length) i.value = i.value + 1;
  else i.value = 0;
};
const prev = () => {
  if (i.value !== 0) i.value = i.value - 1;
  else i.value = filteredImages.value.length;
};

const getCarImage = (img) =>
  new URL(`../../assets/${img}`, import.meta.url).href;

const filteredImages = computed(() =>
  props.images
    .map((img, idx) => ({ img, idx }))
    .filter((t) => t.idx !== i.value)
);
</script>

<template>
  <div class="d-flex flex-column gap-3">
    <div
      class="position-relative overflow-hidden main-image"
      style="border-radius: 8px"
      tabindex="0"
      @keydown.left.prevent="prev"
      @keydown.right.prevent="next"
    >
      <img
        style="object-fit: cover; border-radius: 8px"
        v-if="current"
        :src="getCarImage(current)"
        alt="Zdjęcie samochodu"
        class="w-100 d-block"
        loading="eager"
      />
    </div>
    <div class="d-flex flex-wrap images-wrap">
      <button
        v-for="t in filteredImages"
        :key="t.img"
        type="button"
        class="p-0 border-0 bg-transparent overflow-hidden thumb-btn"
        style="border-radius: 8px"
        @click="select(t.idx)"
      >
        <img
          :src="getCarImage(t.img)"
          alt="Miniatura"
          class="d-block thumb-image"
          loading="lazy"
        />
      </button>
    </div>
  </div>
</template>
<style scoped>
.main-image {
  height: 372px;
}
.thumb-image {
  width: 200px;
  height: 120px;
  object-fit: cover;
}
.images-wrap {
  gap: 30px;
}
@media (max-width: 1120px) {
  .main-image {
    height: auto;
  }
  .images-wrap {
    justify-content: space-between;
  }
}
</style>
