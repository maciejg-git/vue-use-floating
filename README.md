# vue-use-floating

Light composable function for Vue 3 and FloatingUI.

```javascript
let {
  isFloatingVisible: boolean,
  reference: Ref,
  floating: Ref,
  updateFloating: function,
  showFloating: function,
  hideFloating: function,
  toggleFloating: function,
  updateVirtualElement: function,
} = useFloating({
  placement: string,
  offsetX: number,
  offsetY: number,
  flip: boolean,
  autoPlacement: boolean,
  inline: boolean,
  resize: boolean,
})
```
