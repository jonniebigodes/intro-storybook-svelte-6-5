<!-- <script>
  import Task from "./Task.svelte";
  export let loading = false;
  export let tasks = [];

  //👇 Reactive declarations (computed prop in other frameworks)
  $: noTasks = tasks.length === 0;
  $: emptyTasks = noTasks && !loading;
</script>

{#if loading}
  <div class="list-items">loading</div>
{/if}
{#if emptyTasks}
  <div class="list-items">empty</div>
{/if}
{#each tasks as task}
  <Task {task} on:onPinTask on:onArchiveTask />
{/each} -->
<script>
  import PureTaskList from "./PureTaskList.svelte";
  import { taskStore } from "../store";
  function onPinTask(event) {
    taskStore.pinTask(event.detail.id);
  }
  function onArchiveTask(event) {
    taskStore.archiveTask(event.detail.id);
  }
</script>

<PureTaskList
  tasks={$taskStore}
  on:onPinTask={onPinTask}
  on:onArchiveTask={onArchiveTask}
/>
