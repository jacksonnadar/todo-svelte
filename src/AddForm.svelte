<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();
  let inputTodo;
  const addTodo = (e) => {
    e.preventDefault();
    if (!inputTodo) return;
    dispatch('addtodo', {
      id: Math.random().toString(),
      todo: inputTodo,
      completed: false,
    });
    inputTodo = '';
  };
</script>

<style type="text/scss">
  .todo-input-form {
    position: relative;
    background: #232323;

    height: 13%;
    [name='input'] {
      padding: 0 25px;
      height: 100%;
      width: 80%;
      border: none;
      background: #232323;

      font-size: 18px;
      color: #fcf2f2;
    }
    [name='input']:hover {
      opacity: 0.9;
    }
    [name='input']:focus,
    [name='input']:active {
      outline: none;
      border: none;
      opacity: 0.9;
      background: #000000;
    }
    #add-button {
      position: absolute;
      top: 50%;
      right: 25px;
      transform: translateY(-50%);
      color: #232323;
      background: #fcf2f2;
      border-radius: 27px;
      border: none;
      padding: 6px 15px;
      font-weight: bold;
      font-size: 16px;
    }
  }
</style>

<form class="todo-input-form" on:submit={addTodo}>
  <input type="text" name="input" autocomplete="off" bind:value={inputTodo} />
  <button id="add-button" type="submit">ADD</button>
</form>
