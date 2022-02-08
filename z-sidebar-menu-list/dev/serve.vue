<script>
import Vue from 'vue';
import ZSidebarMenuList from '@/z-sidebar-menu-list.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    ZSidebarMenuList
  }
});
</script>

<template>
  <div id="app">
    <z-sidebar-menu-list />
  </div>
</template>
