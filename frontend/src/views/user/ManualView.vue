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
<!-- Tool Tabs -->
        <div class="mb-4 flex flex-wrap gap-2 border-b border-gray-200 pb-3 dark:border-dark-700">
          <button
            v-for="platform in platforms"
            :key="platform.key"
            :class="[
              'rounded-md px-3 py-1.5 text-sm font-medium transition-colors',
              activePlatform === platform.key
                ? 'bg-primary-500 text-white'
                : 'bg-gray-100 text-gray-600 hover:bg-gray-200 dark:bg-dark-800 dark:text-gray-400 dark:hover:bg-dark-700'
            ]"
            @click="activePlatform = platform.key"
          >
            {{ platform.name }}
          </button>
        </div>

        <!-- Codex -->
        <div v-if="activePlatform === 'codex'" class="space-y-3">
          <ManualStep :step="1" :title="t('userManual.codex.step1Title')" :desc="t('userManual.codex.step1Desc')" />
          <ManualStep :step="2" :title="t('userManual.codex.step2Title')" :desc="t('userManual.codex.step2Desc')" />
          <ManualStep :step="3" :title="t('userManual.codex.step3Title')" :desc="t('userManual.codex.step3Desc')" />
          <ManualStep :step="4" :title="t('userManual.codex.step4Title')" :desc="t('userManual.codex.step4Desc')" />
          <ManualStep :step="5" :title="t('userManual.codex.step5Title')" :desc="t('userManual.codex.step5Desc')">
            <code class="rounded bg-gray-100 px-2 py-1 text-xs dark:bg-dark-800">https://api.lxjfly.com</code>
          </ManualStep>
          <ManualStep :step="6" :title="t('userManual.codex.step6Title')" :desc="t('userManual.codex.step6Desc')" />
          <ManualStep :step="7" :title="t('userManual.codex.step7Title')" :desc="t('userManual.codex.step7Desc')" />
          <div class="rounded-lg border-2 border-amber-300 bg-amber-50 p-4 dark:border-amber-700 dark:bg-amber-950/30">
            <p class="text-sm font-semibold text-amber-800 dark:text-amber-300">{{ t('userManual.codex.helpTitle') }}</p>
            <p class="mt-1 text-sm text-amber-700 dark:text-amber-400">{{ t('userManual.codex.helpDesc') }}</p>
          </div>
        </div>

        <!-- Claude Code -->
        <div v-if="activePlatform === 'claude'" class="space-y-3">
          <ManualStep :step="1" :title="t('userManual.claude.step1Title')" :desc="t('userManual.claude.step1Desc')" />
          <ManualStep :step="2" :title="t('userManual.claude.step2Title')" :desc="t('userManual.claude.step2Desc')" />
          <ManualStep :step="3" :title="t('userManual.claude.step3Title')" :desc="t('userManual.claude.step3Desc')">
            <code class="rounded bg-gray-100 px-2 py-1 text-xs dark:bg-dark-800">export ANTHROPIC_BASE_URL=https://api.lxjfly.com</code>
          </ManualStep>
        </div>

        <!-- Gemini CLI -->
        <div v-if="activePlatform === 'gemini'" class="space-y-3">
          <ManualStep :step="1" :title="t('userManual.gemini.step1Title')" :desc="t('userManual.gemini.step1Desc')" />
          <ManualStep :step="2" :title="t('userManual.gemini.step2Title')" :desc="t('userManual.gemini.step2Desc')" />
          <ManualStep :step="3" :title="t('userManual.gemini.step3Title')" :desc="t('userManual.gemini.step3Desc')">
            <code class="rounded bg-gray-100 px-2 py-1 text-xs dark:bg-dark-800">export GEMINI_API_KEY=你的API密钥</code>
          </ManualStep>
          <ManualStep :step="4" :title="t('userManual.gemini.step4Title')" :desc="t('userManual.gemini.step4Desc')">
            <code class="rounded bg-gray-100 px-2 py-1 text-xs dark:bg-dark-800">export GEMINI_API_BASE_URL=https://api.lxjfly.com</code>
          </ManualStep>
        </div>

        <!-- ChatBox -->
        <div v-if="activePlatform === 'chatbox'" class="space-y-3">
          <ManualStep :step="1" :title="t('userManual.chatbox.step1Title')" :desc="t('userManual.chatbox.step1Desc')" />
          <ManualStep :step="2" :title="t('userManual.chatbox.step2Title')" :desc="t('userManual.chatbox.step2Desc')" />
          <ManualStep :step="3" :title="t('userManual.chatbox.step3Title')" :desc="t('userManual.chatbox.step3Desc')" />
          <ManualStep :step="4" :title="t('userManual.chatbox.step4Title')" :desc="t('userManual.chatbox.step4Desc')" />
        </div>
      </div>
    </div>
  </AppLayout>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useI18n } from 'vue-i18n'
import { Icon } from '@/components/icons'
import AppLayout from '@/components/layout/AppLayout.vue'
import ManualStep from '@/components/user/profile/ManualStep.vue'

const { t } = useI18n()

const activePlatform = ref('codex')

const platforms = [
  { key: 'codex', name: 'Codex' },
  { key: 'claude', name: 'Claude Code' },
  { key: 'gemini', name: 'Gemini CLI' },
  { key: 'chatbox', name: 'ChatBox' },
]

//function copyText(text: string) {
  navigator.clipboard.writeText(text)
}
</script>
