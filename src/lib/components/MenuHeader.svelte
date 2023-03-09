<script lang="ts">
	import { page } from '$app/stores';

	export let links: { href: string; label: string }[];

	$: pathname = $page.url.pathname;
</script>

<ul>
	{#each links as link}
		<li>
			<a href={link.href} aria-current={link.href === pathname ? 'page' : undefined}
				>{link.label}
			</a>
		</li>
	{/each}
</ul>

<style>
	ul {
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}

	a {
		padding: 0.5rem;
	}

	a:hover,
	a[aria-current='page'] {
		text-underline-position: under;
		text-decoration-line: underline;
		text-decoration-thickness: var(--underline-thickness, 2px);
		text-underline-offset: var(--underline-offset, 20px);
		text-decoration-color: var(--underline-color, gray);
	}
</style>
