<svelte:options tag="my-component" />
<script>
  import {get_current_component, onMount} from "svelte/internal";
  const component = get_current_component();
  import {writable} from "svelte/store";
  import MySecondComponent from "./MySecondComponent.svelte";

  // example function for dispatching events
  const dispatchEvent = (name, detail) =>
          component.dispatchEvent(new CustomEvent(name, { detail }));
  onMount(() => window.my_store = writable(0))
</script>
<MySecondComponent/>
<button on:click={() => dispatchEvent("test", "Hello!")}>
  Click to dispatch event
</button>
