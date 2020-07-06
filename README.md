# Svelte workshop - Step 1

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

Now we have a list, you can use the checkboxes to mark items, is it over? Do we know everything about Svelte already? Not quite there yet. It's too simple, so let's split that list in two to make it easier to understand what has been acomplished, and also allow the removal of items, to showcase how Svelte controls state and how we can bind events.

### Problem to solve

Display done and todo items in separate lists, and allow the user to remove items from the lists.

### Instructions to achieve the solution

Let's first add a wrapper element to separate the content into two columns:

```html
<div class='board'>
...
</div>
```

And add the board style:
```css
.board {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 1em;
    max-width: 36em;
    margin: 0 auto;
}
```

Now duplicate the list so we can have each part filtered, like this:

```html
<div>
	<h2>Done</h2>
	{#each todos.filter(t => t.done) as todo (todo.id)}
		<label>
			<input type="checkbox">
			{todo.description}
		</label>
	{/each}
</div>
```

This will only display the done items on the second list. You'll need to update the first on to show the not done items, but the secret is in the filter.

To remove the item, we'll need to add a button to each one, and bind it to a method that will update the `todo` list.

First, add a button after the todo description:
```html
<label>
    <input type="checkbox">
    {todo.description}
    <button on:click="{() => remove(todo)}">remove</button>
</label>
```

Note how we binded the call with `on:click`: You can bind to any HTML events like that: `on:mouseover`, `on:enter`, `on:keyup`, etc.

But that's not all: now we need to add the remove method to the `<script>` section:

```javascript
function remove(todo) {
    todos = todos.filter(t => t !== todo);
}
```

It's important to notice that just filtering or updating a single item on the list won't trigger an update in the UI, so we need to re-assign the `todo` variable, since Svelte reactivity is only triggered by assigment.

And, to finish, let's make the items look better by adding some styling:
```css
label {
    position: relative;
    line-height: 1.2;
    padding: 0.5em 2.5em 0.5em 2em;
    margin: 0 0 0.5em 0;
    border-radius: 2px;
    user-select: none;
    border: 1px solid hsl(240, 8%, 70%);
    background-color:hsl(240, 8%, 93%);
    color: #333;
}
input[type="checkbox"] {
    position: absolute;
    left: 0.5em;
    top: 0.6em;
    margin: 0;
}
button {
    position: absolute;
    top: 0;
    right: 0.2em;
    width: 2em;
    height: 100%;
    background: no-repeat 50% 50% url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath fill='%23676778' d='M12,2C17.53,2 22,6.47 22,12C22,17.53 17.53,22 12,22C6.47,22 2,17.53 2,12C2,6.47 6.47,2 12,2M17,7H14.5L13.5,6H10.5L9.5,7H7V9H17V7M9,18H15A1,1 0 0,0 16,17V10H8V17A1,1 0 0,0 9,18Z'%3E%3C/path%3E%3C/svg%3E");
    background-size: 1.4em 1.4em;
    border: none;
    transition: opacity 0.2s;
    text-indent: -9999px;
    cursor: pointer;
}
```

### Expected outcome

The list of items should look like this:
![Image](https://github.com/ladraum/svelte-workshop/raw/step-2/what_to_expect.png)

Now check out the `step-3` branch for the next step.