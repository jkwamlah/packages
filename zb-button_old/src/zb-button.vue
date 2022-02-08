<script>

export default /*#__PURE__*/{
  name: 'ZbButton', // vue component name
  props: {
    buttonStyleObject: {
      type: Object,
      default: () => ({})
    },
    textStyleObject: {
      type: Object,
      default: () => ({})
    },
    buttonType: {
      type: String,
      default: ''
    },
    buttonText: {
      type: String,
      default: ''
    },
    dataToggle: {
      type: String,
      default: ''
    },
    dataTarget: {
      type: String,
      default: ''
    },
    icon: {
      type: String,
      default: ''
    },
    loading: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleButtonClick() {
      this.$emit('button-clicked')
    }
  }
};
</script>

<template>
  <button
      class="z-btn"
      :type="buttonType"
      :style="buttonStyleObject"
      :data-toggle="dataToggle"
      :data-target="dataTarget"
      @click.prevent="handleButtonClick"
  >
    <span v-if="!loading" class="button-text-style" :style="textStyleObject">
      {{ buttonText }}
      <span v-if="icon" class="icon"><i :class="icon"></i></span>
    </span>
    <span v-if="loading">
      <slot name="spinner"></slot>
    </span>
  </button>
</template>

<style scoped>
.z-btn {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  text-decoration: none;
}

.button-text-style {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-style: normal;
  font-weight: 600;
  flex: none;
  order: 0;
  flex-grow: 0;
}

.icon {
  margin-left: 0.93rem;
}

button:focus {
  box-shadow: none;
}
</style>
