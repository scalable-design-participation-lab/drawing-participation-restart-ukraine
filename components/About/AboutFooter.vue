<template>
  <div class="px-7">
    <div class="md:flex place-items-center justify-between">
      <h1 class="text-2xl leading-tight text-zinc-900 dark:text-white">
        <slot name="title"></slot>
      </h1>
      <div class="flex space-x-6 md:pr-2 !place-items-center">
        <a
          v-for="logo in logos"
          :key="logo.url"
          :href="logo.url"
          target="_blank"
        >
          <img
            :src="logo.src"
            :alt="logo.alt"
            class="hover:scale-105 dark:invert"
          />
        </a>
      </div>
    </div>
    <div class="mt-12 md:mt-24 space-y-1 flex flex-col">
      <a
        v-for="link in links"
        :key="link.to"
        :href="link.to"
        class="hover:underline"
      >
        {{ link.label }}
      </a>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Logo {
  url: string
  src: string
  alt: string
}

interface Link {
  to: string
  label: string
}

defineProps<{
  logos: Logo[]
  links: Link[]
}>()
</script>
