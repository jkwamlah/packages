<script>

export default /*#__PURE__*/{
  name: 'ZAvatar',
  props: {
    name: {
      type: String,
      default: ''
    },
    background: {
      type: String,
      default: ''
    }
  },
  computed: {
    getInitials() {
      return this.$props.name.match(/(\b\S)?/g).join("").match(/(^\S|\S$)?/g).join("").toUpperCase()
    }
  }
};
</script>

<template>
  <div class="avatar-wrapper" :style="{background: background}">
    <span class="initials">{{ getInitials }}</span>
  </div>
</template>

<style scoped>
.avatar-wrapper {
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 2.87rem;
  margin-right: 1.37rem;
  display: flex;
  justify-content: center;
}

.initials {
  font-family: Sora;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 140%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #000000;
}
</style>
