<script setup lang="ts">
defineProps<{
  image: string
  class?: string
  backgroundSize?: string
}>()
</script>

<template>
  <div class="slidev-layout image-right grid h-full grid-cols-2">
    <div class="my-auto px-14 py-10">
      <slot />
    </div>
    <div
      class="h-full bg-no-repeat"
      :class="$props.class"
      :style="{
        backgroundImage: `url(${$props.image})`,
        backgroundSize: $props.backgroundSize || 'cover',
      }"
    />
  </div>
</template>
