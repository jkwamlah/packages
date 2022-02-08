<script>
import Vue from 'vue';
import ZSidebar from '@/z-sidebar.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZSidebar
  }
});
</script>

<template>
  <div id="app">
    <z-sidebar />
  </div>
</template>
