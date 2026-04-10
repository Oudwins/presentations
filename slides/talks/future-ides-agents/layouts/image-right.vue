<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
  image: {
    type: String,
  },
  class: {
    type: String,
  },
  contentClass: {
    type: String,
  },
  backgroundSize: {
    type: String,
    default: 'cover',
  },
})

const style = computed(() => ({
  backgroundImage: `url(${props.image})`,
  backgroundRepeat: 'no-repeat',
  backgroundSize: props.backgroundSize,
}))
</script>

<template>
  <div class="grid grid-cols-2 w-full h-full auto-rows-fr">
    <div class="slidev-layout default" :class="props.contentClass">
      <slot />
    </div>
    <div class="w-full h-full" :class="props.class || 'bg-center'" :style="style" />
  </div>
</template>
