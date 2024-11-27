<template>
  <div class="px-7 md:w-9/12 md:max-w-[1100px]">
    <h2 class="mt-12 mb-2 text-3xl">{{ title }}</h2>
    <div class="md:w-9/12 space-y-2 mb-8">
      <slot></slot>
    </div>
    <img v-if="image" :src="image" :alt="imageAlt" :class="imageClass" />
  </div>
</template>

<script setup lang="ts">
defineProps<{
  title: string
  image?: string
  imageAlt?: string
  imageClass?: string
}>()
</script>
