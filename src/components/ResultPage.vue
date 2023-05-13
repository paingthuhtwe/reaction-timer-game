<template>
  <span class="bg-teal-300 px-3 py-2 rounded-lg text-2xl">
    {{ score }}
  </span>
  <h3 class="text-center text-3xl text-slate-700 my-3">
    {{ result }} Try Again in
  </h3>
  <fa class="text-2xl" :icon="['far', 'star']" beat-fade />
  <span class="bg-teal-300 px-4 py-2 rounded-full text-2xl font-semibold mx-3">
    {{ closeTime }}
  </span>
  <fa class="text-2xl" :icon="['far', 'star']" beat-fade />
</template>

<script>
export default {
  props: ["result", "score", "closeTime"],
};
</script>

<style>
</style>