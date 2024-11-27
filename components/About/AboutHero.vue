<template>
  <div class="mt-48 md:w-9/12 md:max-w-[1100px] px-7">
    <img :src="image" :alt="imageAlt" class="w-full rounded-md" />
    <h1 class="mt-12 mb-2 text-3xl">{{ title }}</h1>
    <div class="md:w-9/12 space-y-2">
      <slot></slot>
    </div>
    <div class="flex space-x-2 mt-6">
      <UButton
        v-for="(button, index) in buttons"
        :key="index"
        class="my-2 py-3 px-6 rounded-full flex place-self-start"
        :class="[
          button.secondary
            ? 'bg-gray-300 dark:bg-zinc-600 dark:text-white text-black hover:text-white dark:hover:bg-zinc-700 dark:hover:text-white'
            : 'hover:bg-gray-300 hover:text-black dark:hover:bg-zinc-700 dark:hover:text-white',
        ]"
        color="black"
        :to="button.to"
      >
        {{ button.label }}
      </UButton>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Button {
  label: string
  to: string
  secondary?: boolean
}

defineProps<{
  image: string
  imageAlt?: string
  title: string
  buttons: Button[]
}>()
</script>
