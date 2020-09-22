<script>
  import { createEventDispatcher } from 'svelte';

  export let todo;
  export let index;
  export let removeTodo;
  const dispatch = createEventDispatcher();

  const toggleComplete = () => {
    dispatch('togglecomplets', index);
  };
  let truncate = true;
  const toggleTruncate = () => {
    console.log('clockS');
    truncate = !truncate;
  };
</script>

<style type="text/scss">
  .todo {
    width: 80%;
    font-size: 18px;
    overflow-wrap: break-word;
    hyphens: auto;
  }
  .truncate {
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }
  .line-through {
    text-decoration: line-through;
  }
  .list {
    padding: 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    border-bottom: 0.5px solid rgba(0, 0, 0, 0.3);
    .buttons {
      display: flex;
      flex-direction: row;
      width: 20%;
      justify-content: space-around;
      cursor: pointer;
    }
  }
</style>

<div class="list">
  <div
    on:click={toggleTruncate}
    class="{truncate ? 'truncate' : ''} todo {todo.completed ? 'line-through' : ''}"
    title={todo.todo}>
    {todo.todo}
  </div>
  <div class="buttons">
    <div class="tick" on:click={toggleComplete}>
      <svg
        width="25"
        height="20"
        viewBox="0 0 25 20"
        fill="none"
        xmlns="http://www.w3.org/2000/svg">
        <path d="M2 10.75L9 17L23 2" stroke="#69DE5F" stroke-width="4" />
      </svg>
    </div>
    <div class="cross" on:click={() => removeTodo(todo.id)}>
      <svg
        width="24"
        height="17"
        viewBox="0 0 24 17"
        fill="none"
        xmlns="http://www.w3.org/2000/svg">
        <path d="M2 2L22 15M22 2L2 15" stroke="#EB6A6A" stroke-width="4" />
      </svg>
    </div>
  </div>
</div>
