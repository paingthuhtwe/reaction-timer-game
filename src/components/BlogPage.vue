<template>
  <div
    class="blog w-96 h-64 bg-teal-400 hover:bg-teal-500 cursor-pointer mx-auto my-12 rounded-lg text-xl font-bold text-slate-600 flex items-center justify-center"
    @click="stopPlaying"
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
  methods: {
    stopPlaying() {
      this.$emit("stop");
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlog = !this.showBlog;
    }, this.delay);
  },
  updated() {
    this.showBlog = !this.showBlog;
  },
};
</script>

<style>
</style>