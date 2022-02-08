<script>

export default /*#__PURE__*/{
  name: 'ZSidebarUserAccount',
  data() {
    return {};
  },
  props: {
    width: {
      type: String,
      default: '',
    },
    height: {
      type: String,
      default: '',
    },
    background: {
      type: String,
      default: '',
    },
    account: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {},
  methods: {
    handleDropdownMenuItemClick(menu) {
      this.$emit('account-submenu-clicked', menu)
    },
  },
};
</script>

<template>
  <div :style="account.wrapperStyleObject">
    <div class="dropdown">
      <dl class="list-unstyled p-0">
        <dd class="">
          <div class="d-flex justify-content-between btn btn-toggle rounded text-white"
               data-bs-toggle="collapse"
               data-bs-target="#account-collapse"
               aria-expanded="false"
          >
            <div class="">
              <span :class="account.icon" class="pr-1"></span>
              <span class="profile-user-text">{{ account.user }}</span>
            </div>
            <div>
              <span class="d-flex align-items-center" :style="account.caret.styleClass">
                <i :class="account.caret.icon"></i>
              </span>
            </div>
          </div>
          <div :style="account.dropdownContainer" class="collapse" id="account-collapse">
            <dl v-for="(menu, index) in account.data" :key="index"
                :style="{marginBottom: 0}">
              <dd class="" @click.stop="handleDropdownMenuItemClick(menu)"
                  :style="{height: account.dropdownContainer.height,
                  marginTop: account.data.at(0) ? '0.93rem' : '1.43rem',
                  marginBottom: account.data.at(-1) ? 0 : '1.43rem',
                  }"
              >
                <nuxt-link :to="`/${menu.to}`" class="nav-link">
                  <span class="dropdown-text text-capitalize" :style="account.dropdownTextStyleObject">
                    {{ menu.name }}
                  </span>
                </nuxt-link>
              </dd>
            </dl>
          </div>
        </dd>
      </dl>
    </div>
  </div>
</template>

<style scoped>
.dropdown-text {
  cursor: pointer !important;
  text-decoration: none !important;
}

.nav-link {
  display: block;
  padding: 0.5rem 1rem 0;
}

.collapsing {
  transition: 0.5ms !important;
}
</style>
