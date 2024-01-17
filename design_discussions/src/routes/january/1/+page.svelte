<script>
	import { fade, fly, slide } from 'svelte/transition';
	import myImage from '$lib/screenshot.png?enhanced';

	let clicked = false;
	let alsoClicked = false;
	let clickedAgain = false;
    let hovered = false;
    let alsoHovered = false;

</script>

<h1 in:fly={{ duration: 1200 }} class="text-7xl">FEEDBACK!!!!</h1>

<button on:click={() => (clicked = !clicked)} class="my-3 text-xl cursor-help">
	What is feedback??
</button>

{#if clicked}
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<div class="bg-[#414143] mx-1 my-5 rounded-md text-white px-5 py-5">
		<p in:fly={{ x: -200, y: 200, duration: 500 }} class="text-3xl">
			Feedback - <span class="text-[#BEC1C5] text-xl" in:fly={{ delay: 800 }}
				>communicating the <b class="text-white">results</b>
				of an
				<b
					class="text-white transition hover:text-green-400 cursor-pointer"
					on:click={() => (alsoClicked = !alsoClicked)}>action</b
				></span
			>
			<span class="text-xl" in:fly={{ delay: 1800 }}
				>- is a well known concept from the science of control and information theory.</span
			>
		</p>

		{#if alsoClicked}
			<div in:slide={{ x: 200 }} class="py-8">
				<enhanced:img
					on:click={() => (clickedAgain = !clickedAgain)}
					transition:fade
					src={myImage}
					alt="definition of feedback"
					class=" w-[500px] cursor-pointer"
				/>
			</div>
		{/if}
	</div>
{/if}

{#if clickedAgain}
	<p transition:fade class="text-2xl">
		But i prefer to explain it as something which has notified you about another
	</p>

    <p transition:fade={{delay: 800}} class="text-2xl my-5">
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        For example, how do i know i am saving my content <span on:mouseenter={() => hovered = !hovered}>right</span> {#if hovered}
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <span on:mouseenter={() => alsoHovered = !alsoHovered}>about</span>
        {/if}  {#if alsoHovered}
             <button class=" cursor-wait">now???</button>
        {/if} 
    </p>
{/if}

<div class="min-h-64">

</div>