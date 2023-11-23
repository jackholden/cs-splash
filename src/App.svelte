<script>
  import { invoke } from "@tauri-apps/api/primitives"
  import Greet from './lib/Greet.svelte'
  import { onMount } from "svelte";

  import {getCurrent, Window} from "@tauri-apps/api/window"

const appWindow = getCurrent();

// Creating new windows:
// alternatively, load a remote URL:


function windowTest(){
  const webview = new Window("theUniqueLabel", {
  url: "https://github.com/tauri-apps/tauri",
});
  }

  function loadingTest(){
  const webview = new Window("splashscreen", {
  url: "/public/splashscreen.html",
});
webview.show();
  }

  onMount(async () => {
        // await invoke("close_splashscreen"); -- try to keep splashscreen open
    });
</script>

<main class="container">
  <h1>Welcome to Tauri!</h1>

  <div class="row">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo vite" alt="Vite Logo" />
    </a>
    <a href="https://tauri.app" target="_blank">
      <img src="/tauri.svg" class="logo tauri" alt="Tauri Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank">
      <img src="/svelte.svg" class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>

  <p>
    Click on the Tauri, Vite, and Svelte logos to learn more.
  </p>

  <div class="row">
    <Greet />
    <button on:click={windowTest}>Click me</button>
    <button on:click={loadingTest}>Click me splash</button>
  </div>

</main>

<style>
  .logo.vite:hover {
    filter: drop-shadow(0 0 2em #747bff);
  }

  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00);
  }
</style>
