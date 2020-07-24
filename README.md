# Svelte workshop

![Svelte icon](https://svelte.dev/svelte-logo-horizontal.svg)

This project is a self contained workshop to get started with Svelte. 
Get from zero to having a grasp of what Svelte offers by following the steps in this repository.

This workshop is an overview based on the [Svelte tutorial](https://svelte.dev/tutorial), and it's intended as a quick dive into Svelte, to get a developer quickly up to speed with Svelte and creating the first components right away.

## What you will build?

![What to expect](https://github.com/ladraum/svelte-workshop/blob/main/what_to_expect.gif?raw=true)

Beatiful transitions, captioning effects, all making sure the user feels in control of the application.
Too much trouble to build? Just go through this workshop to see for yourself.

## How to use this repository

This workshop is divided in steps, each with its own branch. Start with the `main` branch, then `step-1`, `step-2`, ... Each branch has a README.md which proposes:

- Problem to solve
- Instructions to achieve the solution
- Expected outcome

For starter, this is the proposition for the first step:

### Problem to solve

How to start a new Svelte project?

### Instructions to achieve the solution

To generate a project, we're going to use a Svelte template, to speed things up and get you right to coding.

```bash
npx degit sveltejs/template my-svelte-workshop
cd my-svelte-workshop
npm install
npm run dev
```

### Expected outcome

Having a Svelte ready project to start coding with. It should look like this:
![Image](https://i.ibb.co/fqkg9wc/svelte-preview.png)

Now check out the `step-1` branch for the next step.

## TLDR

For an even quicker overview, check the differences for each step:

- [Setup](https://github.com/ladraum/svelte-workshop/compare/main...step-1?expand=1#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Display list](https://github.com/ladraum/svelte-workshop/compare/step-1...step-2?expand=1#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Listen to DOM events](https://github.com/ladraum/svelte-workshop/compare/step-2...step-3?expand=1#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Update component State](https://github.com/ladraum/svelte-workshop/compare/step-3...step-4?expand=1#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Add animation](https://github.com/ladraum/svelte-workshop/compare/step-4...step-5#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Passing propertie to child element](https://github.com/ladraum/svelte-workshop/compare/step-5...step-6#diff-534c52cd83756b9c3b6c7b2243edda00)
- [Load data from server and handle loading state](https://github.com/ladraum/svelte-workshop/compare/step-6...final#diff-534c52cd83756b9c3b6c7b2243edda00)