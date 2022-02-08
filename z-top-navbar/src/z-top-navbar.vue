<script>

export default /*#__PURE__*/{
  name: 'ZTopNavbar',
  props: {
    showSearch: {
      type: Boolean,
      default: false,
    },
    showNotificationIcon: {
      type: Boolean,
      default: false,
    },
    setSearchDefault: {
      type: Boolean,
      default: true,
    },
    styleObject: {
      type: Object,
      default: () => ({}),
    },
    bootstrapClass: {
      type: String,
      default: '',
    },
    titleObject: {
      type: Object,
      default: () => ({}),
    },
    searchObject: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {
      search: ''
    };
  },
  computed: {
    getSearchPlaceholder() {
      return !this.search.length || this.$props.setSearchDefault ? 'Search...' : this.search
    }
  },
  methods: {
    handleSearchTerm() {
      this.$emit('search', this.search)
    },

    handleClickNotificationIcon() {
      this.$emit('notification-clicked')
    }
  },
};
</script>

<template>
  <div class="nav-container" :class="bootstrapClass" :style="styleObject">
    <div class="nav-left">
      <div class="z-collapse">
        <nuxt-link :to="`/${titleObject.to}`" class="nav-link px-0">
          <span class="text-capitalize" :style="titleObject.styleClass">
            {{ titleObject.name }}
          </span>
        </nuxt-link>
      </div>

      <div class="search-container" v-if="showSearch">
        <label for="search" class="d-flex mb-0" :class="searchObject.iconStyle">
          <span class="d-flex align-items-center"><i :class="searchObject.icon"></i></span>
        </label>
        <div class="search-input">
          <form @submit.prevent="handleSearchTerm">
            <input id="search" ref="search" class="form-control border-0 p-0" type="search"
                   :placeholder="getSearchPlaceholder"
                   aria-label="Search" v-model="search">
          </form>
        </div>
      </div>
    </div>

    <div class="nav-right">
      <div class="buttons">
        <slot name="buttons"></slot>
      </div>
      <span class="d-flex align-items-center icon-position"
            v-if="showNotificationIcon"
            @click.prevent="handleClickNotificationIcon()"
      >
        <i class="icon-alarm-bell"></i>
      </span>
    </div>
  </div>
</template>

<style scoped>
.nav-container {
  display: flex;
  align-items: center;
  flex-flow: row wrap;
  overflow: hidden;
}

.nav-left {
  position: fixed;
  display: flex;
  margin-left: 1.87rem;
}

.nav-right {
  position: fixed;
  display: flex;
  right: 1.43rem;
}

.search-container {
  display: flex;
  padding-left: 2.25rem;
}

.search-input {
  padding-left: 1.12rem;
}

.buttons {
  display: flex;
}

.form-control:focus {
  -webkit-box-shadow: none;
  box-shadow: none;
}

input[type="search"]::placeholder {
  width: 3.81rem;
  height: 1.25rem;
  font-style: normal;
  font-weight: normal;
  font-size: 0.87rem;
  line-height: 140%;
  color: #B7B7B7;
}

.nav-right {
  position: absolute;
  right: 1.43rem;
}

.icon-position {
  margin-left: 1.87rem;
  cursor: pointer;
}


@media screen and (max-width: 425px) {
  div.nav-container {
    width: 50vw;
  }

  div.z-collapse {
    display: none;
  }

  .search-container {
    display: flex;
    padding-left: 1.25rem;
  }

  .search-input {
    padding-left: 0.5rem;
  }

  .nav-right {
    display: flex;
    right: 0;
  }

  .icon-position {
    margin-left: 0.57rem;
  }
}

@media screen and (min-width: 768px) {
  div.nav-container {
    width: 77vw;
  }

  .nav-right {
    display: flex;
    right: -3.7rem;
  }
}

@media screen and (min-width: 1024px) {
  div.nav-container {
    width: 81vw;
  }

  .nav-right {
    display: flex;
    right: -2.4rem;
  }
}

@media screen and (min-width: 1440px) {
  div.nav-container {
    width: 82.2vw;
  }

  div.nav-right {
    display: flex;
    right: 1.43rem;
  }
}

@media screen and (min-width: 2560px) {
  div.nav-container {
    width: 89.7vw;
  }
}
</style>
