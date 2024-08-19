<script setup>
  import { ref } from 'vue'
  import TheHeader from './components/TheHeader.vue'
  import TheNavigation from './components/TheNavigation.vue'
  import TheTimeline from './pages/TheTimeline.vue'
  import TheActibities from './pages/TheActibities.vue'
  import TheProgress from './pages/TheProgress.vue'
  import { PAGE_TIMELINE, PAGE_ACTIBITIES, PAGE_PROGRESS } from './constants'

  const currentPage = ref(nornalizePageHash())

  function nornalizePageHash() {
    const hash = window.location.hash.slice(1)

    if ([PAGE_TIMELINE, PAGE_ACTIBITIES, PAGE_PROGRESS].includes(hash)) {
      return hash
    }
    window.location.hash = PAGE_TIMELINE

    return PAGE_TIMELINE
  }
</script>

<template>
  <TheHeader />
  <main class="flex flex-grow flex-col">
    <TheTimeline v-show="currentPage === PAGE_TIMELINE" />
    <TheActibities v-show="currentPage === PAGE_ACTIBITIES" />
    <TheProgress v-show="currentPage === PAGE_PROGRESS" />
  </main>
  <TheNavigation :current-page="currentPage" @navigate="currentPage = $event" />
</template>

<style scoped></style>
