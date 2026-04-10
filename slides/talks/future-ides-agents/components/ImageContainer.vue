<script setup lang="ts">
const props = defineProps({
  src: {
    type: String,
    required: true,
  },
  alt: {
    type: String,
    default: '',
  },
  rounded: {
    type: String,
    default: 'lg',
  },
})
</script>

<template>
  <div class="image-container" :class="`rounded-${props.rounded}`">
    <img
      :src="props.src"
      :alt="props.alt"
    />
  </div>
</template>

<style scoped>
.image-container {
  flex: 1 1 0;
  min-height: 0;
  overflow: hidden;
  width: 100%;
  margin-top: 1rem;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 12px;
}

.image-container img {
  width: 100%;
  height: auto;
  display: block;
}
</style>
