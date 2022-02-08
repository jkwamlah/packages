<script>
import Vue from 'vue';
import ZStatusPill from '@/z-status-pill.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZStatusPill
  }
});
</script>

<template>
  <div id="app">
    <z-status-pill />
  </div>
</template>
