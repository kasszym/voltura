<script setup>
import { ref } from "vue";
import ButtonComponent from "../common/ButtonComponent.vue";
import Modal from "../common/Modal.vue";

const props = defineProps({
  car: {
    type: Object,
    required: true,
  },
});

const isDialogOpen = ref(false);

const open = () => (isDialogOpen.value = true);
const close = () => (isDialogOpen.value = false);
defineExpose({ open, close });
</script>
<template>
  <Modal
    v-model:is-open="isDialogOpen"
    :header="car.name"
  >
    <template #content>
      <div>content</div>
    </template>
    <template #footer>
      <ButtonComponent
        title="Anuluj"
        width="100px"
        background-color="#fff"
        color="var(--navy)"
        @handle-click="close"
        :font-weight="400"
        border="1px solid var(--grey)"
      />
      <ButtonComponent
        title="Znajdź dealera"
        width="134px"
      />
    </template>
  </Modal>
</template>
<style scoped></style>
