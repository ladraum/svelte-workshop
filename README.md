# Svelte workshop - Step 6

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

Since we've handled the todo list, let's add something else that is common in applications: loading data from the server. Svelte can handle promisses directly in the HTML, so you don't have to create and handle a separated state just for that.

### Problem to solve

Load a randon number from a server, display a waiting message for the user while loading, and display a message in case of an error.

### Instructions to achieve the solution

Add the code to retrieve the random number in the `<script>` portion:

```javascript
let promise = getRandomNumber();
async function getRandomNumber() {
    const res = await fetch(`https://svelte.dev/tutorial/random-number`);
    const text = await res.text();
    if (res.ok) {
        return text;
    } else {
        throw new Error(text);
    }
}
```

Let's also add a function to trigger it through a button:

```javascript
function handleRandomNumberClick() {
    promise = getRandomNumber();
}
```

Then we the button:

```html
<div>
    <button class="generator" on:click={handleRandomNumberClick}>
        Generate random number
    </button>
</div>
```

And finally display the loaded value:

```html
<div>
    {#await promise}
        ...waiting
    {:then number}
        The number is {number}
    {:catch error}
        <span style="color: red">{error.message}</span>
    {/await}
</div>
```

Using `{#await` we can attach the code directly to the markup. We can even use `{#if`, `{:else}` and `{/if}` for conditionals in the markup too.

### Expected outcome

The list of items should look like this:
![Image](https://github.com/ladraum/svelte-workshop/raw/main/what_to_expect.gif)

If you miss any step, you can check out the `final` branch for the end result.

Thank you for following this workshop!