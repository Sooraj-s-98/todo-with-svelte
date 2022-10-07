<script>
   export let task;
</script>


<div class="task-item mt-2 d-flex justify-content-between align-items-center ">
    <div class="task-name">
        <p 	class="{task.isComplete ? 'text-decoration-line-through' : ''}" id="task__name">{task.content}</p>
    </div>
    <div class="action btns">
        <button type="button" class="btn btn-sm btn-success is__completed" ><i class="fa-solid fa-circle-check"></i></button>
        <button type="button" class="btn btn-sm btn-primary edit" ><i class="fa-solid fa-pen-to-square"></i></button>
        <button type="button" class="btn btn-sm btn-danger ms-1 delete"><i class="fa-solid fa-trash-can"></i></button>
    </div>
</div>