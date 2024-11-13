<template>
  <UModal v-model="isOpen" :ui="modalConfig">
    <div class="space-y-3 p-6">
      <UButton
        v-for="(item, index) in menuItems"
        :key="index"
        block
        :color="item.color || 'white'"
        :variant="item.variant || 'solid'"
        :icon="item.icon"
        :class="[
          'dark:bg-slate-950 dark:text-white text-lg font-semibold rounded-full py-3',
          item.class,
        ]"
        @click="handleItemClick(item)"
      >
        {{ item.label }}
      </UButton>
    </div>
  </UModal>
</template>

<script setup lang="ts">
interface MenuItem {
  label: string
  action: string
  icon?: string
  link?: string
  color?: string
  variant?: string
  class?: string
}

const props = defineProps({
  modelValue: {
    type: Boolean,
    required: true,
  },
  menuItems: {
    type: Array as PropType<MenuItem[]>,
    required: true,
  },
  modalConfig: {
    type: Object,
    default: () => ({
      width: 'w-96',
    }),
  },
})

const emit = defineEmits(['update:modelValue', 'select'])

const isOpen = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value),
})

const handleItemClick = (item: MenuItem) => {
  emit('select', item.action)
  isOpen.value = false
}
</script>
