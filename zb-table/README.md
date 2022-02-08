# Zb-Table
A vue based implementation of modern dynamic tables that bring the best experience and simplicity.
It supports enough props to satisfy mind-blowing customizations.

### Installation
```
npm i zb-table
```
```
yarn add zb-table
```

## Props
```vue
columns: {
  type: Array,
  default: () => ([]),
},

pagination: {
  type: Boolean,
  default: false,
},

numberOfRows: {
  type: String,
  default: '',
},

height: {
  type: String,
  default: '',
}
```

## Usage

```vue
<z-table
    :columns="tableColumns"
    :number-of-rows="tableRows.length.toString()"
    :pagination="true"
  >
    <template>
      <tr
        v-for="(row, rowKey) in tableRows"
        @click.stop="handleShow(rowKey)"
        :style="{marginBottom: setLineAndSpace(rowKey) ? '1.31rem' : '1.25rem',
        paddingBottom: setLineAndSpace(rowKey) ? '1.31rem' : '',
        borderBottom: setLineAndSpace(rowKey) ? '#F3F3F3 0.06rem solid': ''}"
        class="d-flex align-items-center"
      >
        <z-table-data
          width="6%"
        >
          <template>
            <z-switch></z-switch>
          </template>
        </z-table-data>
        <z-table-data
          width="3%"
          :data="row.id"
        />
        <z-table-data
          width="20%"
          :data="row.name"
        />
        <z-table-data
          width="21%"
          :data="row.company"
        />
        <z-table-data
          width="10%"
          :data="row.netSalary"
        />
        <z-table-data
          width="15%"
          :data="row.balance"
        />
        <z-table-data
          width="10%"
          :data="'GHS ' + row.affordability"
        >
          <template>
            <span class="mr-4" @click.prevent="handleIconClicked(rowKey)">
              <i class="icon-pencil"></i>
            </span>
          </template>
        </z-table-data>
        <z-table-data
          width="9%"
          @icon-clicked="handleIconClicked"
        >
          <template>
            <z-pill
              :status="row.approval"
              :background-color="row.approval === 'approved' ? '#F2FDD3' : '#FFE5D4'"
              :status-indicator-color="row.approval === 'approved' ? '#8DE028' : '#FF3C2B'"
            />
          </template>
        </z-table-data>
        <z-table-data
          width="3%"
        >
          <template>
            <z-button
              :buttonStyleObject="kycButtonStyleObject"
              :textStyleObject="kycButtonTextStyleObject"
              button-type="button"
              button-text="view"
            ></z-button>
          </template>
        </z-table-data>
      </tr>
    </template>
  </z-table>
