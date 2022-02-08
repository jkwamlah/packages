<script>
import Vue from 'vue';
import ZMenuBar from '@/z-menu-bar.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZMenuBar
  }
});
</script>

<template>
  <div id="app">
    <z-menu-bar />
  </div>
</template>
