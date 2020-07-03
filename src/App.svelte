<script>
	let uid = 1;

	let todos = [
		{ id: uid++, done: false, description: 'write a Svelte workshop' },
		{ id: uid++, done: false, description: 'start writing blog post' },
		{ id: uid++, done: false, description: 'fix some bugs' },
		{ id: uid++, done: false, description: 'add a feature' },
		{ id: uid++, done: false, description: 'add another feature' },
		{ id: uid++, done: false, description: 'add even another feature' },
	];
</script>

<div>
	<h2>Todo</h2>
	{#each todos as todo (todo.id)}
		<label>
			<input type="checkbox">
			{todo.description}
		</label>
	{/each}
</div>

<style>
	h2 {
		font-size: 2em;
		font-weight: 200;
		user-select: none;
		margin: 0 0 0.5em 0;
	}
</style>