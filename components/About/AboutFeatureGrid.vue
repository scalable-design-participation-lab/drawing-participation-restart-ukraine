<template>
  <div class="px-7 md:flex space-y-3 md:space-x-6 md:space-y-0">
    <div
      v-for="(feature, index) in features"
      :key="index"
      class="p-8 border border-zinc-200 dark:border-zinc-600 md:w-56 min-h-full rounded-xl"
      :class="[index === 0 ? 'pb-32' : '']"
    >
      <h2 class="font-semibold text-xl mb-2">{{ feature.title }}</h2>
      <p class="text-sm leading-tight">{{ feature.description }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Feature {
  title: string
  description: string
}

defineProps<{
  features: Feature[]
}>()
</script>
