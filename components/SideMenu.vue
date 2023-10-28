<script setup lang="ts">
import { gsap } from 'gsap'

const isCollapsed = useMenuState()

const panel = ref<HTMLDivElement | null>(null)
const text = ref<HTMLDivElement | null>(null)

const animateCollapse = () => {
  const tl = gsap.timeline()
  tl.to(text.value, { autoAlpha: 0, display: "none", duration: 0.3 }, '<')
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
  <aside ref="panel" class="panel w-65 h-screen p-4 text-white">
    <button class="item flex items-center w-full min-h-10 mb-4 rounded-lg">
      <Icon name="carbon:user" class="text-xl min-w-10" />
      <span ref="text" class="text-lg text-white pr-2">Account name</span>
    </button>
  </aside>
</template>

<style scoped lang="scss">
.panel {
  background-color: $c-purple;
}

.item {
  background-color: $c-purple-light;
}
</style>
