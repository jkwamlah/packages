# Z-Table-Data
A vue based implementation of modern dynamic table data that brings the best experience and simplicity.
It supports enough props to satisfy mind-blowing customizations.

### Installation
```
npm i z-table-data
```
```
yarn add z-table-data
```

## Props
```vue
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
}
```

## Usage

### Example 1
```vue
<z-table-data
  width="15%"
  data="balance"
/>
```
### Example 2
```vue
<z-table-data
    width="10%"
    :data="'GHS ' + amount"
>
<template>
    <span class="mr-4" @click.stop="handleIconClicked(index)">
      <i class="icon-pencil"></i>
    </span>
</template>
</z-table-data>
```
### Example 3
```vue
<z-table-data
    width="9%"
    @icon-clicked="handlePillClicked"
>
<template>
  <z-pill/>
</template>
</z-table-data>
```



