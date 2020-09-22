<script>
  import AddForm from './AddForm.svelte';

  import SingleTodo from './SingleTodo.svelte';

  let todos = JSON.parse(localStorage.getItem('todos'));
  const addTodoToList = ({ detail }) => {
    todos = [...todos, detail];
    updateLS();
  };
  const toggleComplete = ({ detail }) => {
    let updatedtodos = [...todos];
    updatedtodos[detail].completed = !updatedtodos[detail].completed;
    todos = updatedtodos;
    updateLS();
  };

  const removeTodo = (id) => {
    todos = [...todos].filter((todo) => {
      return todo.id !== id;
    });
    updateLS();
  };

  const updateLS = () => {
    localStorage.setItem('todos', JSON.stringify(todos));
  };
</script>

<style type="text/scss">
  main {
    width: 100%;
    height: calc(100% - 60px);
    display: flex;
    align-items: center;
    justify-content: center;
    .todo-container {
      width: 90%;
      max-width: 544px;
      height: 434px;
      background: #fcf2f2;
      border-radius: 29px;
      display: flex;
      flex-direction: column;
      overflow: hidden;
      .todo-lists {
        height: 88%;
        padding: 10px 0;
        overflow: auto;
      }
    }
  }
</style>

<main>
  <div class="todo-container">
    <div class="todo-lists">
      {#each todos as todo, index}
        <SingleTodo
          on:togglecomplets={toggleComplete}
          {todo}
          {index}
          {removeTodo} />
      {/each}
    </div>
    <AddForm on:addtodo={addTodoToList} />
  </div>
</main>
