# Svelte workshop - Step 4

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

So now we can get items moving, but it's too abrupt. We want to give our users a great user experience so they want to get things done.

### Problem to solve

Ease the transitions for:
- Moving items between Todo and done
- When adding new items
- When removing an item

### Instructions to achieve the solution

The fastest way to ease some of the transitions is to add the `animate` property with the flip option, which is based on [First, Last, Invert, Play](https://aerotwist.com/blog/flip-your-animations/). To use it, first we'll need to import it:

```javascript
import { flip } from 'svelte/animate';
```

Then we can add it to our labels:

```html
<label animate:flip>
    ...
</label>
```

This will make the items remaining items on the list move up, instead of just showing in the new position. But there's more we can do. We want to link the items leaving one list to the ones entering the other, and to do so we'll use `crossfade`. That will allow us to send and receive items across lists. And if we don't have an item (if the user is removing or adding items), we'll need a fallback method to handle that.

So, we'll start by importing:

```javascript
import { crossfade } from 'svelte/transition';
import { quintOut } from 'svelte/easing'; // this is for the fallback method
```

And after that, we can use them to create the `send` and `receive` methods for our transitions:

```javascript
const [send, receive] = crossfade({
    duration: d => Math.sqrt(d * 200),

    fallback(node, params) {
        const style = getComputedStyle(node);
        const transform = style.transform === 'none' ? '' : style.transform;

        return {
            duration: 600,
            easing: quintOut,
            css: t => `
                transform: ${transform} scale(${t});
                opacity: ${t}
            `
        };
    }
});
```
With those created, we can update our labels to use them as:

```html
<label
    in:receive="{{key: todo.id}}"
    out:send="{{key: todo.id}}"
    animate:flip
>
```

This way, we can identify the items going in and out, so the animations can flow.

And, to finalize, we can only show the remove button when the user hovers the item. Since we already have the animation set up, we can do that just by styling the button, not displaying it by default:

```css
button {
    ...
    opacity: 0;
}
label:hover button {
    opacity: 1;
}
```

### Expected outcome

The list of items should look like this:
![Image](https://github.com/ladraum/svelte-workshop/raw/step-4/what_to_expect.gif)

Now check out the `step-5` branch for the next step.