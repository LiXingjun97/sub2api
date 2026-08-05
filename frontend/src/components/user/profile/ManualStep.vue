<template>
  <div class="rounded-lg border border-gray-200 p-4 dark:border-dark-700">
    <div class="flex items-start gap-3">
      <span class="flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-primary-100 text-xs font-bold text-primary-700 dark:bg-primary-900/40 dark:text-primary-300">
        {{ step }}
      </span>
      <div class="space-y-1">
        <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ title }}</p>
        <p class="text-sm text-gray-600 dark:text-gray-400">{{ desc }}</p>
        <slot />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
defineProps<{ step: number; title: string; desc: string }>()
</script>
