<script>
	import { fade, fly, slide } from 'svelte/transition';
	import myImage from '$lib/screenshot.png?enhanced';
	import { onMount } from 'svelte';

	let clicked = false;
	let alsoClicked = false;
	let clickedAgain = false;
	let hovered = false;
	let alsoHovered = false;

	let count = 0;
	let completed = false;

	let characters = ['🎊', '🥳', '🎉', '🍥', '👏', '🍾', '🦞', '🎈'];

	let confetti = new Array(200)
		.fill()
		.map((_, i) => {
			return {
				character:
					characters[i % characters.length],
				x: Math.random() * 100,
				y: -20 - Math.random() * 100,
				r: 0.1 + Math.random() * 1
			};
		})
		.sort((a, b) => a.r - b.r);

	onMount(() => {
		let frame;

		function loop() {
			frame = requestAnimationFrame(loop);

			confetti = confetti.map((emoji) => {
				emoji.y += 0.3 * emoji.r;
				if (emoji.y > 150) emoji.y = -20;
				return emoji;
			});
		}

		loop();

		return () => cancelAnimationFrame(frame);
	});

	function increment() {
		console.log(count);
		if (count >= 10) {
			alert('GEEZ MAN YOUR CONTENT IS DOWNLOADING OKAY!!!!');
		}
		return (count += 1);
	}
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

	<p transition:fade={{ delay: 800 }} class="text-2xl my-5">
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		For example, how do i know i am downloading my content
		<span on:mouseenter={() => (hovered = !hovered)}>right</span>
		{#if hovered}
			<!-- svelte-ignore a11y-no-static-element-interactions -->
			<span on:mouseenter={() => (alsoHovered = !alsoHovered)}>about</span>
		{/if}
		{#if alsoHovered}
			<button on:click={increment}>now???</button>
		{/if}
	</p>

	<a
		transition:fade={{ delay: 1200 }}
		href="https://keep.google.com/u/0/#label/Design%20Discussions"
		class=" decoration-transparent transition hover:text-red-500"
		target="_blank"
		>Let's check out some of the notes!</a
	>
{/if}

<div class="min-h-64"></div>

<h1 class="my-5 text-3xl">Few last thoughts</h1>

<ul class=" list-disc text-xl">
	<li>Haptic feedback</li>
	<li>feedback in terms of surveys</li>
	<li>the importance of feedback in design and in todays world</li>
	<li>everything in this world relies on feedback</li>
</ul>

<button
	on:click={() => (completed = !completed)}
	class=" bg-orange-400 transition hover:bg-orange-600 rounded-sm px-5 py-2 text-white hover:scale-110 my-10"
>
	AND WE'RE DONE!!!! YAYYYY
</button>

{#if completed}
{#each confetti as c}
	<span class="confetti" style="left: {c.x}%; top: {c.y}%; transform: scale({c.r})">
		{c.character}
	</span>
{/each}
{/if}


<style>
	:global(body) {
		overflow-x: hidden;
	}

	.confetti {
		position: absolute;
		font-size: 5vw;
		user-select: none;
	}
</style>
