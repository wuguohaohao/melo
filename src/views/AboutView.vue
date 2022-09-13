<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button id="counter" @click="increment">{{ count }}</button>
    <button v-show="showBtn">SHOW</button>
  </div>
</template>

<script setup lang="ts">
import { nextTick, ref } from "vue";
const count = ref(0);
const showBtn = ref(false);
const increment = async (): Promise<void> => {
  count.value++;
  console.log("nextTick前", document.getElementById("counter")?.textContent);
  await nextTick(() => {});
  console.log("nextTick后", document.getElementById("counter")?.textContent);
};
</script>
<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
