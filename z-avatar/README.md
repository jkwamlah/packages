# Z-Status-Pill
A vue based implementation of modern dynamic avatars that bring the best experience and simplicity.
It supports enough props to satisfy mind-blowing customizations. Get concise avatars with distinct colors and text.

### Installation
> ``` 
> yarn add z-avatar
> ```
>  ```
> npm i z-avatar
> ```


name: {
    type: String,
    default: ''
},
background: {
    type: String,
    default: ''
},
textColor: {
    type: String,
    default: ''
},
avatarStyleObject: {
    type: Object,
    default: () => [{}]
},


## Props
```vue
name: {
  type: String,
  default: '',
},
background: {
  type: String,
  default: '',
},
textColor: {
  type: String,
  default: '',
},
avatarStyleObject: {
  type: Object,
  default: () => [{}],
},
> ```


## Computed
```vue
computed: {
  getInitials()
}
```

## Usage

###Example 1
```vue
<z-table-data
  width="20%"
  :data="row.name"
>
  <template #avatar>
    <z-avatar
    :name="row.name"
    :background="getAvatarBackgroundColor()"
    ></z-avatar>
  </template>
</z-table-data>
```

###Example 2
```vue
<z-avatar
  name="Jonadab Kwamlah"
  background="#FACFE5"
/>
```
