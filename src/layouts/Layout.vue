<script setup lang="ts">
import DotPattern from '@/components/DotPattern.vue'
</script>

<template>
  <div class="flex h-full w-full">
    <DotPattern
      :size="32"
      :radius="1.5"
      :offset-x="0"
      :offset-y="0"
      class="absolute inset-0 h-full w-full fill-white/10 [mask-image:radial-gradient(white,transparent_85%)]"
    >
    </DotPattern>
    <div class="relative mx-auto max-w-7xl">
      <slot />
    </div>
  </div>
</template>
