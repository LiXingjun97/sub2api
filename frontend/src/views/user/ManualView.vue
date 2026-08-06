<template>
  <AppLayout>
    <div class="mx-auto max-w-[950px] space-y-6">
      <!-- Header -->
      <div class="flex items-center gap-3">
        <Icon name="book" size="lg" class="text-primary-500" />
        <h1 class="text-2xl font-bold text-gray-900 dark:text-gray-100">
          {{ t('userManual.title') }}
        </h1>
      </div>

      <!-- Quick Start Table -->
      <div class="card overflow-hidden">
        <div class="border-b border-gray-200 bg-primary-50 px-6 py-4 dark:border-dark-700 dark:bg-primary-950/30">
          <h2 class="text-lg font-semibold text-primary-800 dark:text-primary-200">
            {{ t('userManual.quickStart.title') }}
          </h2>
          <p class="mt-1 text-sm text-primary-600 dark:text-primary-400">
            {{ t('userManual.quickStart.introDesc') }}
          </p>
        </div>
        <div class="divide-y divide-gray-100 dark:divide-dark-700">
          <div class="flex items-start gap-4 px-6 py-4">
            <span class="flex h-7 w-7 shrink-0 items-center justify-center rounded-full bg-primary-500 text-sm font-bold text-white">1</span>
            <div class="min-w-0">
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.quickStart.step1Title') }}</p>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.quickStart.step1Desc') }}</p>
            </div>
          </div>
          <div class="flex items-start gap-4 px-6 py-4">
            <span class="flex h-7 w-7 shrink-0 items-center justify-center rounded-full bg-primary-500 text-sm font-bold text-white">2</span>
            <div class="min-w-0">
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.quickStart.step2Title') }}</p>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.quickStart.step2Desc') }}</p>
            </div>
          </div>
          <div class="flex items-start gap-4 px-6 py-4">
            <span class="flex h-7 w-7 shrink-0 items-center justify-center rounded-full bg-primary-500 text-sm font-bold text-white">3</span>
            <div class="min-w-0">
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.quickStart.step3Title') }}</p>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.quickStart.step3Desc') }}</p>
            </div>
          </div>
          <div class="flex items-start gap-4 px-6 py-4">
            <span class="flex h-7 w-7 shrink-0 items-center justify-center rounded-full bg-primary-500 text-sm font-bold text-white">4</span>
            <div class="min-w-0">
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.quickStart.step4Title') }}</p>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.quickStart.step4Desc') }}</p>
            </div>
          </div>
          <div class="flex items-start gap-4 px-6 py-4">
            <span class="flex h-7 w-7 shrink-0 items-center justify-center rounded-full bg-primary-500 text-sm font-bold text-white">5</span>
            <div class="min-w-0">
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.quickStart.step5Title') }}</p>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.quickStart.step5Desc') }}</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Resources Section -->
      <div class="card p-6">
        <h2 class="mb-3 text-lg font-semibold text-gray-900 dark:text-gray-100">{{ t('userManual.resourceTitle') }}</h2>
        <p class="mb-4 text-sm text-gray-600 dark:text-gray-400">{{ t('userManual.resourceDesc') }}</p>
        <div class="space-y-3">
          <a
            href="https://openai.com/zh-Hans-CN/codex/"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center gap-3 rounded-lg border border-gray-200 p-3 transition-colors hover:border-primary-400 hover:bg-primary-50 dark:border-dark-600 dark:hover:border-primary-600 dark:hover:bg-primary-950/20"
          >
            <span class="flex h-9 w-9 shrink-0 items-center justify-center rounded-lg bg-primary-100 text-primary-600 dark:bg-primary-900/40 dark:text-primary-300">
              <Icon name="download" size="lg" />
            </span>
            <div>
              <p class="text-sm font-semibold text-gray-800 dark:text-gray-200">{{ t('userManual.codexDownload') }}</p>
              <p class="text-xs text-gray-500 dark:text-gray-400">openai.com/codex</p>
            </div>
            <Icon name="externalLink" size="sm" class="ml-auto text-gray-400" />
          </a>
        </div>
      </div>
    </div>
  </AppLayout>
</template>


<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { Icon } from '@/components/icons'
import AppLayout from '@/components/layout/AppLayout.vue'

const { t } = useI18n()
</script>
