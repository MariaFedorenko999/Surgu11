<script>
    export let id;
    export let text;
    export let isDone;
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
</script>
<div class="todo-item" class:todo-item_done={isDone}>
    <input 
      class="todo-item_check" 
      type="checkbox" 
      on:change={dispatch('change', {id})}  
      checked={isDone}
    />
    <span class="todo-item_text">{text}</span>
    <button class="todo-item_btn" on:click={dispatch('remove', {id})}  >Del</button>
</div>
<style>
    .todo-item{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 15px;
        background: red;
    }
    .todo-item_done{
        background: green;
    }
    .todo-item_done.todo-item_text{
        text-decoration: line-through;
    }
    .todo-item_check{

    }
    .todo-item_text{
        flex-grow: 1;
    }
    .todo-item_btn{
        border: none;
        border-radius: 10px;
        background-color: chocolate;
        padding: 10px;
        min-width: 100px;
    }
</style>