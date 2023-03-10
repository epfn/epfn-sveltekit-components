<script lang="ts">
	export let value: string = '';
	export let label: string;
	export let name: string;
	export let required: boolean = false;
	export let readonly: boolean = false;
	export let error: boolean = false;
	export let rows: number = 8;
</script>

<div>
	<label for={'epfn-input-' + name}>{label}</label>
	<textarea
		id={'epfn-input-' + name}
		bind:value
		{name}
		{readonly}
		{required}
		{rows}
		aria-invalid={error}
	/>
</div>

<style>
	div {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		width: 100%;
	}

	label {
		font-weight: 500;
	}

	textarea {
		padding: 0.5rem 0.75rem;
		background-color: var(--background-color, gray);
		border-width: 1px;
		border-style: solid;
		border-color: var(--border-color, gray);
		outline-width: 0;
		outline-style: solid;
		outline-color: var(--border-color, gray);
	}

	textarea:focus-visible {
		outline-width: 1px;
	}

	textarea:disabled,
	textarea:read-only {
		cursor: not-allowed;
	}
</style>
