<script setup lang="ts">
  const props = defineProps({
    class: {
      type: String,
    },
  })
</script>

<template>
  <div class="slidev-layout default flex flex-col">
    <div class="header">
      <slot />
    </div>
    <div class="slidev-layout default flex flex-col justify-center p-0 " :class="class">
        <slot name="centralise" />
    </div>
  </div>
</template>
