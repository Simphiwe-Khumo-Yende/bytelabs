<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { animate, inView } from 'motion'

const el = ref(null)

const props = defineProps({
  delay: { type: Number, default: 0 },
  direction: { type: String, default: 'up' },
  duration: { type: Number, default: 0.7 },
  amount: { type: Number, default: 0.15 },
})

onMounted(() => {
  if (!el.value) return

  const offsets = {
    up:    { y: [24, 0] },
    down:  { y: [-24, 0] },
    left:  { x: [24, 0] },
    right: { x: [-24, 0] },
  }

  const stop = inView(
    el.value,
    ({ target }) => {
      animate(
        target,
        { opacity: [0, 1], ...offsets[props.direction] },
        { duration: props.duration, delay: props.delay, easing: [0.25, 0.1, 0.25, 1] }
      )
    },
    { amount: props.amount }
  )

  onUnmounted(() => stop())
})
</script>

<template>
  <div ref="el" style="opacity: 0">
    <slot/>
  </div>
</template>
