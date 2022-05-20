<script lang="ts">
import Vue from 'vue';
import Vuenicetimeline from '@/vuenicetimeline.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    Vuenicetimeline
  }
});
</script>

<template>
  <div id="app">
    <vuenicetimeline />
  </div>
</template>
