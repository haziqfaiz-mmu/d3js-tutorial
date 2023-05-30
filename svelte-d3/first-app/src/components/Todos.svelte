<script>
    let todos=[
        {id: 1, name:"Create a Svelte Starter App", completed:true},
        {id: 2, name:"Create your first component", completed:true},
        {id: 1, name:"Complete the rest of the tutorial", completed:false}
    ];

    let totalTodos = todos.length;
    let completedTodos = todos.filter((todo)=>todo.completed).length;
</script>

<div class = "todoapp stack-large">
    <form>
        <h2 class="label-wrapper">
            <label for="todo-0" class>
                What need to be done?
            </label>
        </h2>

        <input type="text" id="todo-0" autocomplete="off" class="input input__lg" />
        <button type="submit" disabled="" class="btn btn__primary btn__lg">
            Add
        </button>
    </form>  
    
    <!--Filter-->
    <div class="filters btn-group stack-exception">
        <button class="btn toggle-btn" aria-pressed="true">
            <span class="visually-hidden">Show</span>
            <span>All</span>
            <span class="visually-hidden">tasks</span>
        </button>
        <button class="btn toggle-btn" aria-pressed="false">
            <span class="visually-hidden">Show</span>
            <span>Active</span>
            <span class="visually-hidden">tasks</span>
          </button>
        <button class="btn toggle-btn" aria-pressed="false">
            <span class="visually-hidden">Show</span>
            <span>Completed</span>
            <span class="visually-hidden">tasks</span>
        </button>
    </div>

    <!--To do Status-->
    <h2 id="list-heading">{completedTodos} out of {totalTodos} items complete</h2>
    
    <ul>
        {#each todos as todo, index}
          <li>
            <input type="checkbox" checked={todo.completed}/> {index}. {todo.name} (id: {todo.id})
          </li>
        {:else}
          Nothing to do here!
        {/each}
    </ul>
        
    <!-- To-dos -->
<ul role="list" class="todo-list stack-large" aria-labelledby="list-heading">
    {#each todos as todo,index}
    <li class="todo">
      <div class="stack-small">
        <div class="c-cb">
          <input
            type="checkbox"
            id="todo-{todo.id}"
            checked={todo.completed} />
          <label for="todo-{todo.id}" class="todo-label"> {todo.name} </label>
        </div>
        <div class="btn-group">
          <button type="button" class="btn">
            Edit <span class="visually-hidden">{todo.name}</span>
          </button>
          <button type="button" class="btn btn__danger">
            Delete <span class="visually-hidden">{todo.name}</span>
          </button>
        </div>
      </div>
    </li>
    {:else}
    <li>Nothing to do here!</li>
    {/each}
  </ul>
  
  

  <hr />

  <!-- MoreActions -->
  <div class="btn-group">
    <button type="button" class="btn btn__primary">Check all</button>
    <button type="button" class="btn btn__primary">Remove completed</button>
  </div>
</div>
    
