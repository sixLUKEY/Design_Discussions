<script>
    import { fly } from "svelte/transition";

    let clicked = false;
</script>

<h1 in:fly={{duration: 1200}} class="text-7xl">
    FEEDBACK!!!!
</h1>

<button
on:click={() => clicked = true}
 class="my-3 text-xl cursor-help">
    What is feedback??
</button>

<p class:clicked class="hidden" in:fly={{x: -200, y: 200, duration: 500}} >
    Feedback is bla bla bla
</p>

<style>
    .clicked {
        display: block;
    }
</style>