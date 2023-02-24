<script>
  import TodoForm from "./TodoForm.svelte";
  import TodoList from "./TodoList.svelte";

  // Check local storage
  let todos = localStorage.getItem("todos")
    ? JSON.parse(localStorage.getItem("todos"))
    : [];
  function addTodo(todo) {
    if (!todo) return;
    todos.push({
      title: todo,
      done: false
    });
    todos = todos;
  }
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
    width: 80vw;
    margin: 0 auto;
  }
</style>

<main>
  <h2>Todo List</h2>
  <TodoForm {addTodo}/>
  <TodoList {todos}/>
</main>
