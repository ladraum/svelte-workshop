# Svelte workshop - Step 5

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

Since most of the User Experience is done, let's talk about something to improve the developers experience. Instead of passing every single property to an HTML element, you can use the spread option to do it.

### Problem to solve

Use an JS object to populate the properties of an `<img>` tag.

### Instructions to achieve the solution

We first need to create the JS obejct, like:

```javascript
const LOGO = {
    src: 'http://womenintech-awards.com/wordpress/wp-content/uploads/2019/10/rangle-wit-awards.png',
    alt: 'Rangle.io',
    width: 200,
    height: 140
};
```

Then we can simply spread it on the tag:


```html
<div class="logo-container">
    <img {...LOGO} />
</div>
```

And add some styling to it:

```css
.logo-container {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 1;
    grid-row-end: 1;
    text-align: center;
}
```

That way you don't have to pass every single property separetly.

### Expected outcome

The list of items should look like this:
![Image](https://github.com/ladraum/svelte-workshop/raw/step-5/what_to_expect.gif)

Now check out the `step-6` branch for the next step.