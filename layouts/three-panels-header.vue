<script setup lang="ts">
  const props = defineProps({
    layoutClass: {
      type: String,
    },
    leftClass: {
      type: String,
    },
    middleClass: {
      type: String,
    },
    rightClass: {
      type: String,
    },
  })
</script>

<template>
  <div class="slidev-layout three-cols-header w-full h-full" :class="layoutClass" >
    <div class="col-header">
      <slot />
    </div>
    <div class="col-left" :class="leftClass">
      <slot name="left" />
    </div>
    <div class="col-middle" :class="middleClass">
      <slot name="middle" />
    </div>
    <div class="col-right" :class="rightClass">
      <slot name="right" />
    </div>
    <div class="col-bottom">
      <slot name="bottom" />
    </div>
  </div>
</template>

<style scoped>
.three-cols-header {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
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
  background-color: #f3f4f6; /* Tailwind's bg-gray-100 */
  padding: 1rem; /* Tailwind's p-4 */
  margin: 1.25rem; /* Tailwind's m-5 */
}
.col-middle {
  grid-column: 2;
  grid-row: 2;
  background-color: #f3f4f6; /* Tailwind's bg-gray-100 */
  padding: 1rem; /* Tailwind's p-4 */
  margin: 1.25rem; /* Tailwind's m-5 */
}
.col-right {
  grid-column: 3;
  grid-row: 2;
  background-color: #f3f4f6; /* Tailwind's bg-gray-100 */
  padding: 1rem; /* Tailwind's p-4 */
  margin: 1.25rem; /* Tailwind's m-5 */
}
.col-bottom {
  grid-column: 1 / 4;
  grid-row: 3;
  align-self: end;
}

</style>
