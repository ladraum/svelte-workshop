# Svelte workshop - Step 1

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

Files everywhere! But all in the right and usual places. The src folder will contain the application code. The `main.js` in there will bootstrap the application. But what it that next to it? App.`svelte`? What? Another extension?

Yes. It is required to allow Svelte to process it's content into the lighting fast vanilla JS that will run in the browser.

Let's dissect it for a moment:

- It starts with the `<script>` tag which is the Javascript part of the code. It will contain all logic for that component.
- There is `<main>`, which is the HTML part of the component. In this case, is using the `<main>` [HTML tag](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/main) to display the content, and inside it, the `{name}` binding, which we'll talk more about later.
- And finally the `<style>` portion of it, which is the styles and CSS for the component.

Pretty straighforward, right?

A few things to mention:

In the `<script>` portion, it's exporting the `name` variable. This turns into the component properties. That means, if someone would use this component, they could use it as `<App name="Svelte">` and it would show as `Hello Svelte`. 

That property can be set as defatul in the component, as `export let name = "world"`. That would:
- For `<App>`, would render as `hello world`
- For `<App name="Svelte">`, would render as `hello Svelte`

To add logic to the HTML from the Javascript portion, Svelte uses the the `{#` annotation. Use it with each to display lists of data.

### Problem to solve

Let's display some data. Display a list of Todo items that will be interactive in the future steps.

Let's also style the header of the todos to be a bit better than the standard `<h2>`.

### Instructions to achieve the solution

Replace the script portion of the `App.svelte` file with:

```javascript
let uid = 1;

let todos = [
    { id: uid++, done: false, description: 'write a Svelte workshop' },
    { id: uid++, done: false, description: 'start writing blog post' },
    { id: uid++, done: false, description: 'fix some bugs' },
    { id: uid++, done: false, description: 'add a feature' },
    { id: uid++, done: false, description: 'add another feature' },
    { id: uid++, done: false, description: 'add even another feature' },
];
```

And also replace the style portion with:
```css
h2 {
    font-size: 2em;
    font-weight: 200;
    user-select: none;
    margin: 0 0 0.5em 0;
}
```

And for the display portion, use: 

```html
<div>
	<h2>Todo</h2>
	{#each todos as todo (todo.id)}
		<label>
			<input type="checkbox">
			{todo.description}
		</label>
	{/each}
</div>
```

Note the `{#each todos as todo (todo.id)}`, that can iterate over items and display the content for each one. It uses the `(todo.id)` to identify each of the items to display.

### Expected outcome

The list of items should look like this:
![Image](https://i.ibb.co/74fJ0Xs/step2-start.png)

Now check out the `step-2` branch for the next step.