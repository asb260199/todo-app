<script>
	export let name;

	let todos = []
	let newTodo = ''

	function addTodo (e) {
		e.preventDefault()

		const todoObj = {
			todo: newTodo,
			completed: false
		}
		todos = [...todos, todoObj];
		newTodo = "";
	}
	function completeTodo(e,todo){
		e.preventDefault();
		
		todo.completed = !todo.completed
		todos = todos;
	}
</script>


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.not-complete{
		background-color: #ff3e00;
	}
	.complete{
		background-color: green;
	}

</style>

<h1>To do's</h1>
<input type="text" bind:value={newTodo}>
<button on:click={addTodo}>Add todo</button>

{#if todos.length}
	<h2>All todo's</h2>

	{#each todos as todo}
		<li>{todo.todo} - 
		<button on:click={e => completeTodo(e,todo)} class={todo.completed ? 'complete' : 'not-complete'}>complete</button></li>
	{/each}
{/if}