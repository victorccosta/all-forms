<script lang="ts">
  import "./index.css";
  import "medblocks-ui";
  import "medblocks-ui/dist/shoelace";

  import { Router, Route } from "svelte-routing";
  import Home from "./lib/Home.svelte";
  import { forms } from "./lib/FormList.svelte";
  import FormWrapper from "././lib/FormWrapper.svelte";
</script>

<main class="p-5 md:p-12 flex flex-col gap-5">
  <div class="flex justify-between">
    <a class="flex gap-3" href="/">
      <img src="logo192.png" class="w-8 h-8" alt="" />
      <h1 class="text-2xl font-medium text-gray-700">IntelCare</h1>
    </a>
    
  </div>
  <Router>
    <Route path="/"><Home /></Route>
    {#each forms as form}
      <Route path={form.name.replaceAll(" ", "_")}>
        <FormWrapper id={form.id} component={form.component} name={form.name} />
      </Route>
    {/each}
  </Router>
</main>

<style>
</style>
