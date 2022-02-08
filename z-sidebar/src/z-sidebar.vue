<script>

export default /*#__PURE__*/{
  name: 'ZSidebar', // vue component name

  props: {
    width: {
      type: String,
      default: '',
    },
    height: {
      type: String,
      default: '',
    },
    mainStyleObject: {
      type: Object,
      default: () => ({}),
    },
    annexStyleObject: {
      type: Object,
      default: () => ({}),
    },
    annexContent: {
      type: Object,
      default: () => ({}),
    },
    companies: {
      type: Array,
      default: () => ({}),
    },
    role: {
      type: String,
      default: '',
    },
    roleTextColor: {
      type: String,
      default: '#FFFFFF',
    },
    mainContent: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {}
  },
  computed: {
    getUser: function () {
      return this.role.length > 9 ? this.$props.role.slice(0, 9) + '...' : this.role
    }
  },
  methods: {
    handleCompanyClick(company) {
      this.$emit('company-clicked', company)
    },
  },
};
</script>

<template>
  <div class="sidebar-wrapper">
    <div class="d-flex" :style="{width: width, height: height ? height : '100vh'}">
      <div class="sidebar-annex" :style="annexStyleObject">
        <div class="d-flex">
          <div class="btn p-0">
            <dl class="mb-0" v-for="(company, index) in companies"
                :key="index"
                @click.stop="handleCompanyClick(company)"
            >
              <dt :class="!company.underline ? 'pb-2' : ''">
                <div class="annex-menu-item-container"
                     :style="{ width: company.componentWidth, height: company.componentHeight,
                     background: company.background, borderColor: company.borderColor, border: company.componentBorder}"
                >
                  <span v-if="company.avatar" :style="{color: company.textColor}">
                    <i :class="company.icon"></i>
                  </span>
                  <span v-if="!company.avatar" :style="{color: company.textColor,}">
                    {{ company.initials }}
                  </span>
                </div>
                <span v-if="company.underline">
                  <hr class="separator">
                </span>
              </dt>
            </dl>
          </div>
        </div>
      </div>

      <div>
        <div class="sidebar-main" :style="mainStyleObject">
          <div class="d-flex justify-content-between">
          <span class="sidebar-logo">
            <slot name="logo" class="d-flex"></slot>
          </span>
            <span v-if="role" class="user-role text-capitalize" :style="{color: roleTextColor}">
            {{ getUser }}
          </span>
          </div>
          <div class="">
            <slot name="main-content" class="d-flex"></slot>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<style scoped>
.sidebar-wrapper {
  width: 100% !important;
  padding: 0;
  margin: 0;
  height: 100% !important;
  overflow: hidden;
}

.sidebar-wrapper p {
  margin: 0 0 1em;
}

.sidebar-annex {
  display: flex;
  flex-direction: column;
}

.annex-menu-item-container {
  display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-radius: 5px;
}

.sidebar-main {
  display: flex;
  justify-content: start;
  height: 100%;
  flex-direction: column;
  padding: 1.56rem 0 0 0
}

.sidebar-logo {
  width: 6.4rem;
  height: 1.25rem;
  padding-left: 0.5rem;
}

.user-role {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.7rem 1rem 0 0;
  font-style: normal;
  font-weight: 600;
  font-size: 10px;
  line-height: 140%;
  width: auto;
}

.separator {
  width: 1.9rem !important;
  height: 0.063rem !important;
  background: #23414e !important;
  padding: 0
}

@media {
  .sidebar-wrapper {
    width: 100%
  }
}
</style>
