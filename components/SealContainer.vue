<template>
  <img id="seal-container" v-on:load="updateGradient" :src="seal"></img>
</template>
<style lang="stylus">
  #seal-container
    max-width: 95vw
    max-height: 50vh
    border: 8px solid #FFFFFF
    border-radius: 6px
    box-shadow: 0px 2px 4px #000000
</style>
<script>
  import Grade from 'grade-js';

  export default {
    name: 'SealContainer',
    props: {
      seal: String,
    },
    methods: {
      updateGradient() {
        // hacks
        setTimeout(()=> {
          try {
            Grade(document.body, '#seal-container');
          } catch(e) { }
        }, 100);
      },
    },
    ready() {
      this.updateGradient();
    },
    watch: {
      seal() {
        this.updateGradient();
      },
    },
  };
</script>
