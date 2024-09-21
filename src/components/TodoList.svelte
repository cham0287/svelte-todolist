<script lang="ts">
  type Todo = {
    id: number;
    text: string;
    completed: boolean;
  };

  let todos: Todo[] = [
    { id: 1, text: "우유 사기", completed: false },
    { id: 2, text: "운동하기", completed: true },
    { id: 3, text: "코딩 공부하기", completed: false },
    { id: 4, text: "책 읽기", completed: false },
  ];

  const toggleTodo = (id: number) => {
    todos = todos.map(todo => 
      todo.id === id ? {...todo, completed: !todo.completed} : todo
    );
  }
</script>

<div>
  <h1>Svelte Todo List</h1>
  <ul>
    {#each todos as todo (todo.id)}
    <li>
      <input
        type="checkbox"
        checked={todo.completed}
        on:change={() => toggleTodo(todo.id)}
      />
      <span class:completed={todo.completed}>
        {todo.text}
      </span>
    </li>
    {/each}
  </ul>
</div>

<style>
  .completed {
    text-decoration: line-through;
  }
  li {
    display: flex;
    align-items: center;
    gap: 8px;
  }
</style>