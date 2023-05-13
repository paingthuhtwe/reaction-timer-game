<template>
  <div
    class="blog w-96 h-64 bg-teal-400 hover:bg-teal-500 cursor-pointer mx-auto my-12 rounded-lg text-xl font-bold text-slate-600 flex items-center justify-center"
    @click="$emit('stop')"
    v-if="showBlog"
  >
    Click Here
    {{ delay }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      showBlog: false,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlog = !this.showBlog;
      this.$emit("timer");
    }, this.delay);
  },
  updated() {
    this.showBlog = !this.showBlog;
  },
  unmounted() {
    this.$emit("showResult");
  },
};
</script>

<style>
</style>