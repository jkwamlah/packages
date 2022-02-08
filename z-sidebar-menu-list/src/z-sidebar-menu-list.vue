<script>

export default /*#__PURE__*/{
  name: 'ZSidebarMenuList',
  props: {
    menuCategories: {
      type: Array,
      default: () => ([]),
    },
    default: {
      type: String,
      default: '',
    },
    marginTop: {
      type: String,
      default: '',
    },
    height: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      menuName: ''
    }
  },
  methods: {
    handleMenuItemClick(menu) {
      this.menuName = menu.name
      this.$emit('menu-item-clicked', menu)
    },
    handleSubMenuItemClick(subMenu) {
      this.$emit('sub-menu-item-clicked', subMenu)
    }
  },
  mounted() {
    this.menuName = this.$props.default
  }
};
</script>

<template>
  <div class="scroll" :style="{marginTop: marginTop, height: height ? height : '30.35rem'}">

    <dl v-for="(category, index) in menuCategories"
        :key="index"
        @click.stop="handleMenuItemClick(index)"
    >
      <div v-if="category.categoryName" class="category">{{ category.categoryName }}</div>

      <dl class="list-unstyled p-0"
          v-for="(menu, index) in category.data"
          :key="index"
          @click.stop="handleMenuItemClick(menu)"
      >
        <dd class="">
          <div class="btn btn-toggle rounded text-white"
               data-bs-toggle="collapse"
               :data-bs-target="'#'+menu.name"
               aria-expanded="false"
          >
            <div class="menu-item">
              <span class="d-flex align-items-center pr-2"
                    :style="{color:  menu.name === menuName ? menu.iconSelectedColor : menu.color}">
                <i :class="menu.name === menuName ? menu.iconSelected : menu.icon"></i>
              </span>
              <span class="d-flex align-items-center text-capitalize menu-text"
                    :style="{color: menu.name === menuName ? menu.iconSelectedColor : '#B7B7B7', paddingBottom: 0}"
              >
                  {{ menu.name }}
                </span>
            </div>

            <div v-if="menu.hasSubMenu" :style="menu.subMenuDropdownContainer" class="submenu collapse" :id="menu.name">
              <dl v-for="(subMenu, index) in menu.subMenuItems" :key="index" :style="{marginBottom: 0}">
                <dd @click.stop="handleSubMenuItemClick(subMenu)"
                    :style="{height: menu.subMenuDropdownContainer.height,
                      marginTop: subMenu.at(0) ? '0.93rem' : '1.43rem',
                      marginBottom: subMenu.at(-1) ? 0 : '1.43rem'}"
                >
                  <nuxt-link :to="`/${subMenu.to}`" class="nav-link">
                      <span class="dropdown-text text-capitalize" :style="menu.subMenuDropdownTextStyleObject">
                        {{ subMenu.name }} something else
                      </span>
                  </nuxt-link>
                </dd>
              </dl>
            </div>
          </div>
        </dd>
      </dl>
    </dl>
  </div>
</template>

<style scoped>
.dropdown-text {
  cursor: pointer !important;
  text-decoration: none !important;
}

.nav-link {
  display: flex;
  padding: 0.5rem 1rem 0;
}

.collapsing {
  transition: 0.5ms !important;
}


.tab-left-bar {
  background: #35FF69;
  border-radius: 0 0.63rem 0.63rem 0;
  height: 1.69rem;
  width: 0.063rem;
}

.scroll {
  overflow-x: hidden;
  overflow-y: auto;
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.scroll::-webkit-scrollbar {
  display: none;
}

.nav-link {
  display: block;
}

.category {
  height: 0.87rem;
  padding: 1.87rem 0 1.87rem 1.25rem;
  font-family: Sora;
  font-style: normal;
  font-weight: 600;
  font-size: 0.62rem;
  line-height: 140%;
  letter-spacing: 0.03em;
  text-transform: uppercase;
  color: #707070;
}

.menu-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 1.06rem;
  margin: 0;
  padding-left: 0.25rem;
  color: #B7B7B7;
}

.menu-text {
  height: 1.06rem;
  font-family: Sora;
  font-style: normal;
  font-weight: normal;
  font-size: 0.75rem;
  line-height: 140%;
  flex: none;
  order: 1;
  flex-grow: 0;
}

.submenu {
  border-left: 0.043rem solid;
  padding-top: 0.068rem;
  margin-left: 0.71rem;
  margin-bottom: 0;
  height: 1.4rem;
}
</style>
