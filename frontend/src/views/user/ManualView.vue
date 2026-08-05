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

      <!-- API Info Card -->
      <div class="card p-6">
        <div class="flex items-start gap-3">
          <Icon name="key" size="sm" class="mt-0.5 shrink-0 text-blue-600 dark:text-blue-400" />
          <div class="space-y-2 text-sm text-blue-800 dark:text-blue-300">
            <p class="font-semibold">{{ t('userManual.apiKeyTitle') }}</p>
            <p>{{ t('userManual.apiKeyDesc') }}</p>
            <div class="flex items-center gap-2">
              <code class="rounded bg-blue-100 px-2 py-0.5 text-xs text-blue-900 dark:bg-blue-900/40 dark:text-blue-200">
                {{ t('userManual.baseUrl') }}: https://api.lxjfly.com
              </code>
              <button
                class="rounded bg-blue-200 px-1.5 py-0.5 text-xs text-blue-700 hover:bg-blue-300 dark:bg-blue-800 dark:text-blue-300 dark:hover:bg-blue-700"
                :title="t('common.copy')"
                @click="copyText('https://api.lxjfly.com')"
              >
                {{ t('common.copy') }}
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Platform Tabs -->
      <div class="card p-6">
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

        <!-- Quick Start -->
        <div v-if="activePlatform === 'quickstart'" class="space-y-4">
          <div class="rounded-lg border border-primary-200 bg-primary-50 p-5 dark:border-primary-800 dark:bg-primary-950/30">
            <h3 class="text-base font-bold text-primary-800 dark:text-primary-200">{{ t('userManual.quickStart.introTitle') }}</h3>
            <p class="mt-2 text-sm leading-relaxed text-primary-700 dark:text-primary-300">{{ t('userManual.quickStart.introDesc') }}</p>
          </div>
          <ManualStep :step="1" :title="t('userManual.quickStart.step1Title')" :desc="t('userManual.quickStart.step1Desc')" />
          <ManualStep :step="2" :title="t('userManual.quickStart.step2Title')" :desc="t('userManual.quickStart.step2Desc')" />
          <ManualStep :step="3" :title="t('userManual.quickStart.step3Title')" :desc="t('userManual.quickStart.step3Desc')" />
          <ManualStep :step="4" :title="t('userManual.quickStart.step4Title')" :desc="t('userManual.quickStart.step4Desc')" />
          <ManualStep :step="5" :title="t('userManual.quickStart.step5Title')" :desc="t('userManual.quickStart.step5Desc')" />
          <div class="rounded-lg border-2 border-amber-300 bg-amber-50 p-4 dark:border-amber-700 dark:bg-amber-950/30">
            <p class="text-sm font-semibold text-amber-800 dark:text-amber-300">{{ t('userManual.codex.helpTitle') }}</p>
            <p class="mt-1 text-sm text-amber-700 dark:text-amber-400">{{ t('userManual.codex.helpDesc') }}</p>
          </div>
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

const activePlatform = ref('quickstart')

const platforms = [
  { key: 'quickstart', name: t('userManual.quickStart.title') },
  { key: 'codex', name: 'Codex' },
  { key: 'claude', name: 'Claude Code' },
  { key: 'gemini', name: 'Gemini CLI' },
  { key: 'chatbox', name: 'ChatBox' },
]

function copyText(text: string) {
  navigator.clipboard.writeText(text)
}
</script>
