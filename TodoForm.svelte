<script>
  export let addTodo;
  let newTodo = "";
  function formSubmit() {
    addTodo(newTodo);
    newTodo = "";
  }
</script>

<form on:submit|preventDefault={formSubmit}>
  <label>
   <strong>
    Add New Todo
   </strong>
    <input placeholder="Enter a new todo..." bind:value={newTodo}>
  </label>
  <br>
  <button>Add Todo</button>
</form>