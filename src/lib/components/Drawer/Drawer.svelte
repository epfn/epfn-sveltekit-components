<script lang="ts">
	import { browser } from '$app/environment';
	import { setContext } from 'svelte';
	import { fade, fly } from 'svelte/transition';

	export let width = 260;
	export let duration = 150;
	export let position: 'left' | 'right' = 'left';

	let isExpanded = false;
	setContext('closeDrawer', { closeDrawer: () => (isExpanded = false) });

	$: if (browser) {
		const body = document.documentElement.querySelector('body');
		if (body) body.style.overflowY = isExpanded ? 'hidden' : 'unset';
	}
</script>

<svelte:window
	on:resize={(event) => {
		if (isExpanded) {
			const prev = event.currentTarget.innerWidth;
			setTimeout(() => {
				if (prev !== event.currentTarget.innerWidth) isExpanded = false;
			}, 500);
		}
	}}
/>

<div class="epfn-drawer">
	<button
		type="button"
		aria-controls="main-menu"
		aria-label="Main Menu Button"
		aria-expanded={isExpanded}
		on:click={() => (isExpanded = !isExpanded)}
	>
		{#if isExpanded}
			<slot name="button-close">Close</slot>
		{:else}
			<slot name="button-open">Open</slot>
		{/if}
	</button>

	{#if isExpanded}
		<div
			class="backdrop"
			transition:fade={{ duration }}
			on:keydown={() => null}
			on:click={() => (isExpanded = false)}
		/>
		<div
			class="content"
			id="main-menu"
			style="width: {width}px; {position}: 0"
			transition:fly={{
				x: position === 'left' ? -width : width,
				duration: duration + 100,
				opacity: 1
			}}
		>
			<slot name="content"><div style="background-color: white;" /></slot>
		</div>
	{/if}
</div>

<style>
	.epfn-drawer {
		display: flex;
		align-items: center;
		isolation: isolate;
		z-index: 10;
	}

	button {
		position: relative;
		z-index: 2;
		-webkit-tap-highlight-color: rgba(255, 255, 255, 0);
	}

	.backdrop {
		position: fixed;
		z-index: -1;
		top: 0;
		left: 0;
		background-color: var(--backdrop-color, rgba(0, 0, 0, 0.75));
		height: 100%;
		width: 100%;
		cursor: pointer;
	}

	.content {
		position: fixed;
		z-index: 1;
		top: 0;
		height: 100%;
		overflow-y: auto;
		display: grid;
	}
</style>
