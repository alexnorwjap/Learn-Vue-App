<script setup>
import { ref } from 'vue'
import NavItem from './NavItem.vue'
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'

const navItems = {
  timeline: ClockIcon,
  actibities: ListBulletIcon,
  progress: ChartBarIcon
}

const currentPage = ref('')
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="justife-around flex items-center border-t">
      <NavItem
        v-for="(icon, page) in navItems"
        :key="page"
        :href="`#${page}`"
        :class="{ 'pointer-events-none bg-gray-200': currentPage === page }"
        @click="currentPage = page"
      >
        <component :is="icon" class="h-6 w-6" />{{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
