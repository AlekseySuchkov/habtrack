<script setup>
import { CheckCircleIcon } from "@heroicons/vue/24/solid";
</script>
<template>
  <a href="#" class="flex items-center text-sm">
    <div v-if="false" class="flex items-center gap-1">
      Day complete!
      <CheckCircleIcon class="5 h-7 text-green-500" />
    </div>
    <div v-else class="flex items-center gap-1">
      <div>Progress: <span class="font-mono">20%</span></div>
      <div class="h-3 w-3 rounded-full bg-red-500"></div>
    </div>
  </a>
</template>
