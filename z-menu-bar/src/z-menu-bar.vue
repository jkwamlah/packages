<script>

export default /*#__PURE__*/{
  name: 'ZMenuBar',
  props: {
    wrapperStyleObject: {
      type: Object,
      default: () => ({})
    },
    showMenuItems: {
      type: Boolean,
      default: false
    },
    menus: {
      type: Array,
      default: () => ({})
    },
    defaultMenuColor: {
      type: String,
      default: ''
    },
    activeMenuColor: {
      type: String,
      default: ''
    },
    defaultActiveMenu: {
      type: String,
      default: ''
    },
    defaultBadgeBackground: {
      type: String,
      default: ''
    },
    activeBadgeBackground: {
      type: String,
      default: ''
    },
  },
  data() {
    return {
      activeMenu: '',
      menuWidth: ''
    }
  },
  methods: {
    getFormattedMenuName(name) {
      return name.replace(/\s+/g, '-').toLowerCase()
    },
    handleMenuClick(menu) {
      this.activeMenu = menu.name
      const name = this.getFormattedMenuName(this.activeMenu)
      this.menuWidth = (document.getElementById(name).offsetWidth * 0.0625) + 'rem'
      this.$emit('menu-clicked', menu)
    }
  },
  mounted() {
    if (this.$props.showMenuItems) {
      this.activeMenu = this.$props.defaultActiveMenu
      this.menuWidth = (document.getElementById(this.getFormattedMenuName(this.activeMenu)).offsetWidth * 0.0625) + 'rem'
    }
  }
};
</script>

<template>
  <div class="menubar-wrapper d-flex justify-content-between" :style="wrapperStyleObject">
    <div v-if="showMenuItems" class="nav border-0 nav-margin">
      <dl v-for="(menu, index) in menus" :key="index" :style="{marginBottom: 0}">
        <div :id="getFormattedMenuName(menu.name)">
          <dd @click.stop="handleMenuClick(menu)">
            <div v-if="activeMenu === menu.name" class="link-active position-absolute"
                 :style="{color: activeMenuColor, width: menuWidth}">
            </div>
            <nuxt-link :to="`/${menu.to}`" class="nav-link d-flex justify-content-center">
              <span class="menu-text text-capitalize"
                    :style="{color: activeMenu === menu.name ? activeMenuColor : defaultMenuColor,
                    fontWeight: activeMenu === menu.name ? '600' : ''}"
              >{{ menu.name }}</span>
              <span class="z-badge" :style="{
                color: activeMenu === menu.name ? activeMenuColor : defaultMenuColor,
                background:  activeMenu === menu.name ? activeBadgeBackground : defaultBadgeBackground
              }"
              >{{ menu.badgeCount }}</span>
            </nuxt-link>
          </dd>
        </div>
      </dl>
    </div>

    <div class="menu-right">
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.menubar-wrapper {
  margin: 0;
  padding: 0;
  border: 0;
}

.nav-margin {
  margin-left: 1.96rem;
}

.menu-text {
  font-style: normal;
  font-size: 0.75rem;
  line-height: 140%;
  display: flex;
  align-items: center;
  margin-right: 0.62rem;
}

.z-badge {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0 0.5rem;
  height: 1.06rem;
  border-radius: 0.25rem;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 140%;
  flex: none;
  order: 0;
  flex-grow: 0;
  margin: 0;
  text-align: center;
  white-space: nowrap;
  transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out, border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.link-active {
  display: flex;
  justify-content: center;
  margin-left: -0.10rem;
  margin-top: 2.69rem !important;
  border-bottom: 3px solid;
  border-radius: 10px 10px 0 0;
  height: 2px;
}

.menu-right {
  position: absolute;
  right: 0;
}

dl dt, dd {
  display: inline;
}

</style>

