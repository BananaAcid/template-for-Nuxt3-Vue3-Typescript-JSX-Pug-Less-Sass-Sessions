<template lang="pug">
section
  p
    b hi
    br
    NuxtLink(to="/two")
      | to page Two

  
  div(ref="div")
    button(@click="sayHi") say hi using JSX
  p 
  
  SessionTests
</template>

<script lang="tsx">
import { render } from "vue"; // for jsx

export default defineComponent({
  data() {
    return {
      n: <div>did say hi</div>,
    };
  },

  async mounted() {},

  methods: {
    sayHi() {
      render(this.n, this.$refs.div as HTMLDivElement); // append
    },
  },
});
</script>

<style lang="less" scoped>
section {
  > div {
    border: 1px solid gray;
    padding: 0.5em 1em;
  }
}
</style>
