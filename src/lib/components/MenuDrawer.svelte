<script lang="ts">
	import { page } from '$app/stores';
	import { getContext } from 'svelte';

	export let links: { href: string; label: string }[];

	const { closeDrawer } = getContext<{ closeDrawer: () => void }>('closeDrawer');

	$: pathname = $page.url.pathname;
</script>

<ul>
	{#each links as link}
		<li>
			<a
				href={link.href}
				aria-current={link.href === pathname ? 'page' : undefined}
				on:click={() => closeDrawer()}>{link.label}</a
			>
		</li>
	{/each}
</ul>

<style>
	ul {
		display: flex;
		flex-direction: column;
	}

	li {
		display: flex;
		border-color: var(--border-color, gray);
		width: 100%;
	}

	li:not(:last-child) {
		border-bottom-width: 1px;
	}

	a {
		width: 100%;
		padding-top: 0.75rem;
		padding-bottom: 0.75rem;
	}

	a:hover,
	a[aria-current='page'] {
		font-weight: 500;
	}
</style>
