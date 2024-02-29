<script setup lang="ts">
import MotionText from '@/components/MotionText.vue'
import { onMounted, ref } from 'vue'

const text = 'Hi, I am Bartłomiej Cisek'
const isActive = ref(false)

onMounted(() => {
  setTimeout(() => {
    isActive.value = true
  }, 500)
})
</script>

<template>
  <MotionText v-slot="{ tokens }" :body="text" mode="symbol">
    <h1 class="max-w-xl text-center text-4xl font-bold">
      <span
        v-for="(token, index) in tokens"
        :key="index"
        :style="{
          '--delay': `${index * 20}ms`
        }"
        :class="{
          'translate-y-8 opacity-0': !isActive,
          'delay-[--delay]': isActive
        }"
        class="inline-block whitespace-pre-wrap transition-[transform,opacity] duration-150"
      >
        {{ token }}
      </span>
    </h1>
  </MotionText>
</template>
