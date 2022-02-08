# Z-Menu-Bar
A vue based implementation of modern dynamic navbar that bring the best experience and simplicity.
It supports enough props to satisfy mind-blowing customizations.

## Usage

## Props
> ```
> wrapperStyleObject: {
>   type: Object,
>   default: () => ({})
> },
>
> showMenuItems: {
>   type: Boolean,
>   default: false
> },
>
> menus: {
>  type: Array,
>  default: () => ({})
> },
> 
> defaultMenuColor: {
>  type: String,
>  default: ''
> },
> 
> activeMenuColor: {
>   type: String,
>   default: ''
> },
> 
> defaultActiveMenu: {
>   type: String,
>   default: ''
> },
> 
> defaultBadgeBackground: {
>   type: String,
>   default: ''
> },
> 
> activeBadgeBackground: {
>   type: String,
>   default: ''
> },
> 
> ```

## Methods
- getFormattedMenuName()
- handleMenuClick()
