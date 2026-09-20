<!-- layouts/grid-cards.vue -->
<script setup lang="ts">
import { useAttrs, useSlots, computed } from 'vue'

const attrs = useAttrs()
const slots = useSlots()

// 1. Collect all card slots dynamically and sort them numerically
const cardSlotKeys = computed(() => {
  return Object.keys(slots)
    .filter(key => key.startsWith('card-'))
    .sort((a, b) => parseInt(a.split('-')) - parseInt(b.split('-')))
})

// 2. Safely read column specifications or use intelligent fallbacks
const columnsCount = computed(() => {
  if (attrs.cols) return parseInt(attrs.cols as string)
  const count = cardSlotKeys.value.length
  return count <= 4 ? 2 : 3 // Automatic sizing: 2-column or 3-column split
})
</script>

<template>
  <div class="slidev-layout default h-full flex flex-col justify-between">
    <!-- Slide Header Area -->
    <div>
      <slot name="default" />
    </div>

    <!-- Controlled Layout Canvas Grid -->
    <div 
      class="grid gap-3 my-auto w-full"
      :style="{ 
        gridTemplateColumns: `repeat(${columnsCount}, minmax(0, 1fr))` 
      }"
    >
      <!-- Standardized layout styling applied universally to all card blocks -->
      <div 
        v-for="slotKey in cardSlotKeys" 
        :key="slotKey"
        class="p-3 bg-slate-50 dark:bg-neutral-800 rounded-xl border border-slate-200 dark:border-neutral-700 shadow-sm flex flex-col justify-between text-xs"
      >
        <slot :name="slotKey" />
      </div>
    </div>
  </div>
</template>