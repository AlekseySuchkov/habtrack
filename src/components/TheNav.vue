<script setup>
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from "../constants";
import { ref } from "vue";
import NavItem from "./NavItem.vue";
import {
  ClockIcon,
  ListBulletIcon,
  ArrowTrendingUpIcon,
} from "@heroicons/vue/24/outline";
const navItems = {
  [PAGE_TIMELINE]: ClockIcon,
  [PAGE_ACTIVITIES]: ListBulletIcon,
  [PAGE_PROGRESS]: ArrowTrendingUpIcon,
};
const currentPage = ref(normalizePageHash());
console.log(currentPage);
function normalizePageHash() {
  const hash = window.location.hash.slice(1);
  if (Object.keys(navItems).includes(hash)) {
    return hash;
  }
  window.location.hash = PAGE_TIMELINE;

  return PAGE_TIMELINE;
}
</script>
<template>
  <nav class="botom-0 sticky bottom-0 z-10">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(icon, page) in navItems"
        :key="page"
        :href="`#${page}`"
        :class="{ 'pointer-events-none bg-gray-200': page === currentPage }"
        v-on:click="currentPage = page"
      >
        <component :is="icon" class="h-6 w-6" />{{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
