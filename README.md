# Svelte workshop - Step 3

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

But I can't get the items to done? This doesn't work! I can check them, but they don't get to the second column.

Don't worry. That step was to understand how to listen to events and how to bind those. Now we'll interact with the items on the list, mark them as done, and see them moving around (and understand how to bind inputs).

### Problem to solve

Allow the users to add items, and move them to done.

### Instructions to achieve the solution

To get the items marked as done, we'll need to update the `todo` list every time the user interacts with the item. Do to that, let's trigger the change for the todo item:

```html
<input type=checkbox on:change={() => mark(todo, true)}>
```

And add the function to make the update. Lets reuse the `remove` function, so the changed item gets moved to the end of the list:

```javascript
function mark(todo, done) {
    todo.done = done;
    remove(todo);
    todos = todos.concat(todo);
}
```

You'll need to add a similar change to the done items, but marking them as not done, and displaying the checkbox as checked.

To allow the user to add a new item, let's add an input that will add the item :

```html
<input
    placeholder="what needs to be done?"
    on:keydown={e => e.key === 'Enter' && add(e.target)}
>
```

This way, the function will only be called when the user presses the `Enter` key. To update the state, we'll need to add the `add` function. We want the item to be added in the start of the list, so we can acomplish this by:

```javascript
function add(input) {
    const todo = {
        id: uid++,
        done: false,
        description: input.value
    };
    todos = [todo, ...todos];
    input.value = '';
}
```

And let's add some style to the input and for the done items:

```css
.board > input {
    font-size: 1.4em;
    grid-column: 1/3;
}
.done {
    border: 1px solid hsl(240, 8%, 90%);
    background-color:hsl(240, 8%, 98%);
}
```

### Expected outcome

The list of items should look like this:
![Image](https://github.com/ladraum/svelte-workshop/raw/step-3/what_to_expect.gif)

Now check out the `step-4` branch for the next step.