<script setup lang="ts">
const isCollapsed = useMenuState()
</script>

<template>
  <div class="w-full h-20 text-black p-4">
    <button class="flex justify-center items-center" @click="isCollapsed = !isCollapsed">
      <Icon name="carbon:up-to-top" class="text-xl -rotate-90" :class="{ 'rotate-90': isCollapsed }" />
    </button>
  </div>
</template>
