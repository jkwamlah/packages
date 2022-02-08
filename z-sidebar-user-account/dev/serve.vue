<script>
import Vue from 'vue';
import ZSidebarUserAccount from '@/z-sidebar-user-account.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZSidebarUserAccount
  }
});
</script>

<template>
  <div id="app">
    <z-sidebar-user-account />
  </div>
</template>
