<script setup lang="ts">
import NavGroup from './NavGroup.vue'
import NavItem from './NavItem.vue'
import NavList from './NavList.vue'
const items = [
  { name: 'Home', href: '/' },
  { name: 'About', href: '/about' },
  { name: 'Projects', href: '/projects' },
  { name: 'Contact', href: '/contact' }
]

function navigate() {
  // the callback is fired once the animation is completed
  // to allow smooth transition
}
</script>

<template>
  <header class="flex h-[100px] w-full items-center px-8">
    <NavGroup
      v-slot="{ ready, size, position, duration }"
      as="nav"
      class="relative mx-auto rounded-2xl bg-white/5 p-4"
    >
      <div class="relative">
        <div
          v-if="ready"
          :style="{
            '--size': size,
            '--position': position,
            '--duration': duration
          }"
          class="absolute inset-y-0 left-0 h-full w-[--size] translate-x-[--position] rounded-lg bg-white/10 transition-[width,transform] duration-[--duration]"
        />

        <NavList as="ul" class="relative flex items-center gap-3">
          <NavItem
            v-for="(item, index) in items"
            :key="index"
            v-slot="{ setActive, isActive }"
            as="li"
            @activated="navigate"
          >
            <RouterLink
              :to="item.href"
              :class="[isActive ? 'text-white' : 'text-white/60 hover:text-white']"
              class="inline-block px-4 py-1 text-sm transition font-semibold"
              @click.prevent="setActive"
              >{{ item.name }}</RouterLink
            >
          </NavItem>
        </NavList>
      </div>
    </NavGroup>
  </header>
</template>
