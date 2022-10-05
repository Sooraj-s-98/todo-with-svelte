<script>
  import { Router, Route, navigate } from "svelte-routing";
  import { onMount } from "svelte";
  import SignUp from "./pages/SignUp.svelte";
  import Login from "./pages/Login.svelte";
  import { user } from "./store/index";
  import api from "./api/index";


  export let url = "";
  let isLoading = true;

 async function fetchAccount(){
    const account = await api.getAccount();
    user.update(() => account);
  }


  onMount(async () => {
    console.log("user", $user)
    if(!$user){
      fetchAccount()
    }
    else{
      navigate("/login");
    }
  });

  isLoading = false;

  $: $user && console.log("user",$user)
</script>

<main>

  <Router {url}>
    <div class="container-fluid px-0">
      {#if isLoading}
        <div class="row min-vh-100 justify-content-center align-items-center">
          <div class="spinner-border text-center" role="status" />
        </div>
      {:else}
        <Route path="/signup" component={SignUp} />
        <Route path="/login" component={Login} />
          <Route path="/"  >
            hello
          </Route>
      {/if}
    </div>
  </Router>

</main>
