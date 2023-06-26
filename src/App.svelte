<script>
  let todos = [{ done: false, message: "do dishes" }];

  function add() {
    todos = todos.concat({ done: false, message: "" });
  }

  function clear() {
    todos = todos.filter((t) => !t.done);
  }

  $: remaining = todos.filter((t) => !t.done).length;
</script>

<h2>Todo List</h2>
{#each todos as todo}
  <div class:done={todo.done}>
    <input type="checkbox" bind:checked={todo.done} />
    <input
      type="textbox"
      placeholder="what needs to be done?"
      bind:value={todo.text}
    />
  </div>
{/each}

<button on:click={add}>Add new</button>
<button on:click={clear} disabled>Clear</button>

<p>{remaining} remaining</p>

<style>
  .done {
    opacity: 0.4;
  }
</style>
