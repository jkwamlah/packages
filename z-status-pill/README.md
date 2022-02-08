# Z-Status-Pill
A vue based implementation of modern dynamic pills that bring the best experience and simplicity.
It supports enough props to satisfy mind-blowing customizations. Communicate concise statuses with distinct colors and text.

### Installation
> ``` 
> yarn add z-status-pill
> ```
>  ```
> npm i z-status-pill
> ```

## Props
> ```vue
> status: {
>   type: String,
>   default: '',
> },
> statusIndicatorColor: {
>   type: String,
>   default: '',
> },
> backgroundColor: {
>   type: String,
>   default: '',
> },
> width: {
>   type: String,
>   default: '',
> },
> ```

## Usage

```vue
<z-status-pill
    :status="success"
    :background-color="'#F2FDD3'"
    :status-indicator-color="'#8DE028'"
/>
