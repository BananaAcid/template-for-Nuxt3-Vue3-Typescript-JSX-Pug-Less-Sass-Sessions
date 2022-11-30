<template lang="pug">
section
  p
    b hi
    br
    NuxtLink(to="/two")
      | to page Two

  
  div(ref="div")
    button(@click="sayHi") say hi
    
  div
    button(@click="updateSession") update using session: {{sessionObj?.session?.test}} / {{val?.test}}
    button(@click="updateSession2") change session
</template>

<script lang="tsx">
import { render } from "vue"; // for jsx

export default defineComponent({
  data() {
    return {
      n: <div>did say hi</div>,

      sessionObj: null,
      val: 0,
    };
  },

  async mounted() {
    // https://nuxt.com/modules/session
    let sessionObj = await useSession();

    this.sessionObj = sessionObj;
    this.val = sessionObj.session;
  },

  methods: {
    sayHi() {
      render(this.n, this.$refs.div as HTMLDivElement); // append
    },

    async updateSession() {
      // must update with an object
      await this.sessionObj.update({ test: 123 });
    },
    async updateSession2() {
      // must update with an object
      await this.sessionObj.update({ test: 456 });
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
