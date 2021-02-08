<script>
	let todos = [
		{ done: false, text: 'finish Svelte tutorial' },
		{ done: false, text: 'build an app' },
		{ done: false, text: 'world domination' }
	];

	function add() {
		todos = todos.concat({ done: false, text: '' });
	}

	function clear() {
		todos = todos.filter(t => !t.done);
	}

	$: remaining = todos.filter(t => !t.done).length;
</script>

<style>
	h1 {
		color: red;
		font-family: "Times New Roman", Times, serif;
		font-style: oblique;
		margin-left: 25px;
		margin-bottom: 30px
}

	div {
		height: 60px;
  	width: 40%;
		margin-left: 10px;
	}
	
	p {
		font-size: 24px;
		font-weight: bold;
		font-style: oblique;
		color: red;
		font-family: "Times New Roman", Times, serif;
		margin-left: 25px;
	}
	
	input {
		border: 2px solid black;
  	border-radius: 5px;
		font-family: "Times New Roman", Times, serif;
	}
	
	button {
		border: 2px solid black;
  	border-radius: 5px;
		margin-left: 25px;
	}
	
</style>

<h1>Todos</h1>

{#each todos as todo}
	<div>
		<input
			type=checkbox
			bind:checked={todo.done}
		>

		<input
			placeholder="What needs to be done?"
			bind:value={todo.text}
			disabled={todo.done}
		>
	</div>
{/each}

<p>{remaining} remaining</p>

<button on:click={add}>
	Add new
</button>

<button on:click={clear}>
	Clear completed
</button>