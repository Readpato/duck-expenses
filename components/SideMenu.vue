<script setup lang="ts">
import { gsap } from 'gsap'

const isCollapsed = ref(false)

const panel = ref<HTMLDivElement | null>(null)
const text = ref<HTMLDivElement | null>(null)

const animateCollapse = () => {
  const tl = gsap.timeline()
  tl
    .to(text.value, { autoAlpha: 0, display: "none", duration: 0.3 }, '<')
    .to(panel.value, { width: 72, duration: 0.3 })
}

const animateExpand = () => {
  const tl = gsap.timeline()
  tl.to(panel.value, { width: 260, duration: 0.3 })
    .to(text.value, { autoAlpha: 1, display: "block" })
}

watch(isCollapsed, (v) => v ? animateCollapse() : animateExpand())

</script>

<template>
  <aside ref="panel" class="panel w-65 h-screen p-4 text-white relative">
    <button class="flex items-center mb-4 min-h-10 relative">
      <Icon name="carbon:user" class="text-xl min-w-10" />
      <span ref="text" class="text-lg text-white">Account name</span>
    </button>
    <button class="flex justify-center items-center absolute bottom-4 right-4" @click="isCollapsed = !isCollapsed">
      <Icon name="carbon:up-to-top" class="text-xl -rotate-90" :class="{ 'rotate-90': isCollapsed }" />
    </button>
  </aside>
</template>

<style scoped lang="scss">
.panel {
  background-color: $c-purple;
}
</style>
