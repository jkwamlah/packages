<script>

export default /*#__PURE__*/{
  name: 'ZStatusPill',
  props: {
    status: {
      type: String,
      default: '',
    },
    statusIndicatorColor: {
      type: String,
      default: '',
    },
    backgroundColor: {
      type: String,
      default: '',
    },
    width: {
      type: String,
      default: '',
    },
  },
};
</script>

<template>
  <div class="row">
    <div class="col-lg-12">
      <div
          class="status-pill d-flex align-items-center justify-content-center"
          :style="{ background: backgroundColor ? backgroundColor : '#DBF5F6', width: width }"
      >
        <div
            class="status-pill-indicator"
            :style="{ background: statusIndicatorColor ? statusIndicatorColor : '#23414E' }"
        ></div>
        <div class="pill-text">
          {{ status }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.status-pill {
  height: 1.56rem;
  padding: 2px 8px;
  border-radius: 1.56rem;
}

.status-pill-indicator {
  width: 0.43rem;
  height: 0.43rem;
  border-radius: 50%;
  margin-right: 0.63rem;
}

.pill-text {
  font-style: normal;
  font-weight: normal;
  font-size: 0.75rem;
  line-height: 140%;
  display: flex;
  align-items: center;
  color: #23414E;
  flex: none;
  order: 1;
  flex-grow: 0;
  text-transform: capitalize;
}
</style>
