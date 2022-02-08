<script>
import Vue from 'vue';
import ZbTable from '@/zb-table.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZbTable
  }
});
</script>

<template>
  <div id="app">
    <zb-table />
  </div>
</template>
