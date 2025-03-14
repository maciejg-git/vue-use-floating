# vue-use-floating

Light Vue 3 composable function to position elements like dropdown, popovers and tooltips. 

[FloatingUI](https://floating-ui.com/) is used to calculate element positions. You can install it with npm:

```bash
npm install @floating-ui/dom
```

[Example on Stackblitz](https://stackblitz.com/edit/vue-use-floating?file=src%2FApp.vue)

# Usage:

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

### Argument:

Function takes single object with FloatingUI options:

- `placement`: is one of the [FloatingUI placement](https://floating-ui.com/docs/computePosition#placement) options. Default: `"bottom-start"`
- `offsetX`: lets you displace a floating element from its reference element. Default: `0`
- `offsetY`: lets you displace a floating element from its reference element. Default: `0`
- `flip`: changes the placement of a floating when it's scheduled to overflow a given boundary. Default: `false`
- `autoPlacement`: chooses the placement that has the most space available automatically. Default: `false`
- `inline`: improves positioning for inline reference elements that span over multiple lines, such as hyperlinks or range selections. Default: `false`
- `resize`: resizes floating element to match width of reference element. Default: `false`

### Returns:

In return we get object with following properties:

- `isFloatingVisible` - controls visibility state of floating element and should be used as a condition for `v-if`/`v-show`
- `reference` - is `template ref` that should be set as `ref` on reference element. If not set Virtual element is used as reference.
- `floating` - is `template ref` that should be set as `ref` on floating element
- `showFloating`, `hideFloating` and `toggleFloating` - functions that control visibility state of floating element
- `updateFloating` - can be used to calculate new position and update floating element
- `updateVirtualElement` - updates virtual element

### Virtual Element

Virtual element allow setting position of floating element relative to a custom reference area, useful for context menus, range selections, following the cursor, and more. Virtual element is used automatically if the reference template ref is not set in the template.

### Example:

```vue
<template>
  <button 
    ref="reference" 
    @click="toggleFloating"
  >
    Floating reference
  </button>

  <div 
    v-if="isFloatingVisible"
    ref="floating"
  >
    Floating content
  </div>
</template>

<script setup>
import useFloating from "use-floating"

let {
  isFloatingVisible,
  reference,
  floating,
  toggleFloating,
} = useFloating({
  placement: "bottom",
  offsetY: 5,
  flip: true,
  autoPlacement: false,
})
</script>
```
