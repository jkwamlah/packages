<script>

export default /*#__PURE__*/{
  name: 'ZbTable',
  props: {
    columns: {
      type: Array,
      default: () => ([])
    },
    rowData: {
      type: Array,
      default: () => ([])
    },
    pagination: {
      type: Boolean,
      default: false
    },
    numberOfRows: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      height: '',
      paginate: false,
      endOfPage: false
    }
  },
  methods: {
    getColumnWidth(value) {
      return this.$props.columns.map((column) =>
          this.getStringCamelCase(column.name) === value ? column.width : '').filter((element) => element !== '')
    },
    getColumnSpan(key) {
      return this.$props.columns.map((column) =>
          this.getStringCamelCase(column.name) === key ? column.span : '').filter((element) => element !== '')
    },
    getStringCamelCase(text) {
      text = text.replace(/[-_\s.]+(.)?/g, (_, c) => c ? c.toUpperCase() : '');
      return text.substr(0, 1).toLowerCase() + text.substr(1);
    },
    setLineAndSpace(index) {
      return (index + 1) % 2 === 0
    },
    handleTableScroll(event) {
      const element = event.target
      const height = element.scrollHeight - element.scrollTop

      return height === Number(element.clientHeight) ? this.endOfPage = true : this.endOfPage = false
    },
    handleClick(type, key) {
      return this.$emit('data-click', {type: type, key: key})
    },
  },
};
</script>

<template>
  <div id="table" class="table-wrapper">
    <table class="table table-borderless" :style="{height: height}">
      <thead>
      <tr class="table-head">
        <th scope="col" class="pl-0 text-capitalize" v-for="column in columns" :style="{ width: column.width }">
          {{ column.name }}
        </th>
      </tr>
      </thead>
      <tbody style="height: calc(100vh - 15.20rem)" @scroll="handleTableScroll">
      <slot></slot>
      <tr v-if="rowData" v-for="(row, rowKey) in rowData" class="d-flex"
          :class="setLineAndSpace(rowKey) ? '' : 'underline'"
      >
        <td
            v-for="(value, dataKey ) in Object.keys(row)"
            class="pl-0 d-flex align-items-center"
            :colspan="getColumnSpan(value)"
            :style="{width: getColumnWidth(value)}"
        >
          <div class="switch" v-if="typeof(row[value]) === 'object' && row[value].type === 'switch'">
            <input type="checkbox" :checked="row[value].checked" :value="dataKey"/>
            <span class="slider round" @click.prevent="handleClick(row[value].type, dataKey)"></span>
          </div>

          <span v-if="typeof(row[value]) === 'object' && row[value].type === 'icon'">
            {{ row[value].value }}
            <i :class="row[value].name" @click.prevent="handleClick(row[value].type, dataKey )"></i>
          </span>

          <span v-if="typeof(row[value]) !== 'object'" class="table-text">{{ row[value] }}</span>
        </td>
      </tr>
      </tbody>
      <caption v-if="pagination" class="caption-container d-flex align-items-center">
        <span v-if="endOfPage" class="caption"> end of page - {{ numberOfRows }} results</span>
      </caption>
    </table>
  </div>
</template>

<style scoped>
.table-wrapper {
  margin: 0 1.87rem 1.18rem;
  border: 0;
}

.table-head {
  height: 3.93rem;
  font-style: normal;
  font-weight: bold;
  font-size: 0.75rem;
  line-height: 140%;
  display: flex;
  align-items: center;
  color: #23414E;
  border-bottom: #F3F3F3 0.06rem solid;
}

.underline {
  margin: 0 0 1.31rem 0;
  border-bottom: #F3F3F3 0.06rem solid;
}

.caption-container {
  bottom: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 3.87rem !important;
  left: 17.9rem !important;
  right: 1.87rem !important;
}

.caption {
  font-style: normal;
  font-weight: 600;
  font-size: 0.62rem;
  line-height: 140%;
  display: flex;
  align-items: center;
  letter-spacing: 0.03em;
  text-transform: uppercase;
  color: #B7B7B7;
}

table {
  -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
  -moz-box-sizing: border-box; /* Firefox, other Gecko */
  box-sizing: border-box; /* Opera/IE 8+ */
}

tbody {
  display: block;
  padding-top: 1.18rem;
  overflow-x: hidden;
  -ms-overflow-style: none; /* for Internet Explorer, Edge */
  scrollbar-width: none; /* for Firefox */
  overflow-y: scroll;
}

tbody::-webkit-scrollbar {
  display: none; /* for Chrome, Safari, and Opera */
}
</style>
