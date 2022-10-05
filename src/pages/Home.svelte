<script>
    import TodoItem from "../components/TodoItem.svelte";
    import api from "../api/index";
    import { user } from "../store/index";


 async function logOut(){
        await api.deleteCurrentSession();
        user.update(() => null);
    }

</script>


<div class="container">
    <div class="row justify-content-center">
        <div class="col-md-6 mt-4 content">
            <div class="card">
                <div class="card-header d-flex justify-content-between">
                    <span class="title-card">
                        To-do List
                    </span>
                    <div id="refresh" title="Refresh"><i class="fa-solid fa-arrow-rotate-right"></i></div>
                </div>
                <div class="card-body">
                    <form action="" class="form d-flex justify-content-between">
                        <input type="text" id="task" class="form-control" placeholder="What's on your Mind?"
                            title="Write a Task..." />
                        <div class="d-flex">
                            <button type="button" id="create-task" class="btn btn-primary ms-2"
                                title="Create">Create</button>
                            <button type="button" id="search-task" class="btn btn-success ms-2"
                                title="Search">Search</button>
                        </div>
                    </form>

                    <div id="tasks">

                        <TodoItem />
                        <TodoItem />
                    </div>

                    <div id="search"></div>
                </div>
            </div>
            <div class="error"></div>
            <div class="clear__all btn btn-danger btn-lg d-none">Clear All</div>
        </div>
    </div>
    <button type="button" class="btn btn-primary ms-2" on:click={logOut} ><i class="fa fa-sign-out"></i></button>
</div>