<script setup>
  import NavItem from './NavItem.vue'
  import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
  import { PAGE_TIMELINE, PAGE_ACTIBITIES, PAGE_PROGRESS } from '../constants'

  defineProps(['currentPage'])

  const emit = defineEmits(['navigate'])

  const navItems = {
    [PAGE_TIMELINE]: ClockIcon,
    [PAGE_ACTIBITIES]: ListBulletIcon,
    [PAGE_PROGRESS]: ChartBarIcon,
  }
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="justife-around flex items-center border-t">
      <NavItem
        v-for="(icon, page) in navItems"
        :key="page"
        :href="`#${page}`"
        :class="{ 'pointer-events-none bg-gray-200': currentPage === page }"
        @click="emit('navigate', page)">
        <component :is="icon" class="h-6 w-6" />{{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
