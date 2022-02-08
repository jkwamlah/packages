<script>
import Vue from 'vue';
import ZTableData from '@/z-table-data.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZTableData
  }
});
</script>

<template>
  <div id="app">
    <z-table-data />
  </div>
</template>
