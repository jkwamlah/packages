<script>

export default /*#__PURE__*/{
  name: 'ZTableData',
  props: {
    data: {
      type: String,
      default: '',
    },
    dataType: {
      type: String,
      default: '',
    },
    colspan: {
      type: String,
      default: '',
    },
    width: {
      type: String,
      default: '',
    },
  },
  methods: {
    setLineAndSpace(index) {
      return (index + 1) % 2 === 0
    },
  },
};
</script>

<template>
  <td
      class="pl-0 data-wrapper d-flex align-items-center"
      :colspan="colspan"
      :style="{ width: width }"
  >
    <span v-if="dataType === 'icon'" class="d-flex mr-12" @click.prevent="$emit('icon-clicked')">
      <i class="d-flex align-items-center icon-pointer" :class="data"></i>
    </span>
    <span v-if="data && !dataType" class="d-flex table-text mr-12">{{ data }}</span>
    <slot></slot>
  </td>
</template>

<style scoped>
.data-wrapper {
  padding: 0;
  cursor: pointer;
}

.table-text {
  height: 1.06rem;
  font-style: normal;
  font-weight: 400;
  font-size: 0.75rem;
  line-height: 140%;
  display: flex;
  align-items: center;
  color: #000000;
}

.mr-12 {
  margin-right: 0.75rem;
}
</style>
