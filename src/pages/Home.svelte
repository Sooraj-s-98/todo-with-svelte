<script>
  import { onMount } from "svelte";
  import TodoItem from "../components/TodoItem.svelte";
  import api from "../api/index";
  import { user } from "../store/index";

  let content = "";
  let tasks=[];

  async function logOut() {
    await api.deleteCurrentSession();
    user.update(() => null);
  }

  async function handleAddTodo() {
    const userId = $user["$id"];
    if (!userId || !content) {
      console.log("User id is null/empty");
    } else {
      const data = {
        content: content,
        isComplete: false,
        date: new Date(),
      };

      await api.createDocument(data);
      content = "";
      getTodoList();
    }
  }

  async function getTodoList() {
    const listDocumentRes=await api.listDocuments();
    if(listDocumentRes.documents){
        tasks=listDocumentRes.documents;
    }
  }

  onMount(async () => {
    getTodoList();
  });
</script>

<div class="container">
  <div class="row justify-content-center">
    <div class="col-md-6 mt-4 content">
      <div class="card">
        <div class="card-header d-flex justify-content-between">
          <span class="title-card"> To-do List </span>
          <div id="refresh" title="Refresh">
            <i class="fa-solid fa-arrow-rotate-right" />
          </div>
        </div>
        <div class="card-body">
          <form action="" class="form d-flex justify-content-between">
            <input
              type="text"
              bind:value={content}
              id="task"
              class="form-control"
              placeholder="What's on your Mind?"
              title="Write a Task..."
            />
            <div class="d-flex">
              <button
                type="button"
                id="create-task"
                class="btn btn-primary ms-2"
                title="Create"
                on:click={handleAddTodo}>Create</button
              >
              <button
                type="button"
                id="search-task"
                class="btn btn-success ms-2"
                title="Search">Search</button
              >
            </div>
          </form>
          {#each tasks as task}

            <TodoItem {task}/>
            {/each}

          <div id="search" />
        </div>
      </div>
      <div class="error" />
      <div class="clear__all btn btn-danger btn-lg d-none">Clear All</div>
    </div>
  </div>
  <button type="button" class="btn btn-primary ms-2" on:click={logOut}
    ><i class="fa fa-sign-out" /></button
  >
</div>
