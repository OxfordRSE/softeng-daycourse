<!--

Example usage:
---
layout: instruction
leftClass: "items-start justify-start"
rightClass: "items-end justify-end"
---

Note that class names are tailwindcss classes

-->
<script setup lang="ts">
  const props = defineProps({
    layoutClass: {
      type: String,
    },
    leftClass: {
      type: String,
    },
    rightClass: {
      type: String,
    },
  })
</script>

<template>
  <div class="slidev-layout two-cols-header w-full h-full gap-4" :class="layoutClass" >
    <div class="col-header">
      <slot />
    </div>
    <div class="col-left flex flex-col justify-center" :class="leftClass">
      <slot name="left" />
    </div>
    <div class="col-right bg-gray-100 dark:bg-gray-600 dark:border dark:border-color-gray-400 p-2" :class="rightClass">
      <slot name="right" />
    </div>
    <div class="col-bottom">
      <slot name="bottom" />
    </div>
  </div>
</template>

<style scoped>
.two-cols-header {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: auto 1fr auto;
  height: 100%;
}

.col-left, .col-middle, .col-right {
  display: flex;
  flex-direction: column;
}

.col-header {
  grid-column: 1 / 4;
}
.col-left {
  grid-column: 1;
  grid-row: 2;
}
.col-right {
  grid-column: 2;
  grid-row: 2;
}
.col-bottom {
  grid-column: 1 / 4;
  grid-row: 3;
  align-self: end;
}

</style>
