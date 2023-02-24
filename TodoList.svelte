<script>
  export let todos;

  function removeTodo(index) {
    todos.splice(index, 1);
    todos = todos;
  }

  $: localStorage.setItem("todos", JSON.stringify(todos));
</script>

<style>
  ul {
    text-align: left;
    cursor: pointer;
  }

  li {
    list-style-type: none;
  }
  .done {
    text-decoration: line-through;
    text-decoration-color: red;
  }
  .todotitle {
    width: 150px;
    display: inline-block;
  }
  .mark {
    display: inline-block;
    width: 30px;
  }
  .delete {
    display: inline-block;
    width: 50px;
  }
  .delete:hover {
    transform: scale(1.3);
  }
  hr {
    border: 0.9px solid black;
  }
</style>

{#if todos.length > 0}
    <hr>
    <br>
    <ul>
      {#each todos as todo, index}
        <li>
          <span class:done={todo.done} class="todotitle" on:click={()=>todo.done = !todo.done}>
            {todo.title} 
          </span>
          <span class="mark" on:click={()=>todo.done = !todo.done}>
            {#if todo.done }
              ✅
            {:else}
              &xcirc;
            {/if}
          </span>
          <span class="delete" on:click={()=>removeTodo(index)} >
            🗑  
          </span>
        </li>
      {/each}
    </ul>
{/if}

