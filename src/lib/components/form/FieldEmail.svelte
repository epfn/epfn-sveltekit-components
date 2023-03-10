<script lang="ts">
	export let value: string = '';
	export let label: string;
	export let name: string;
	export let required: boolean = false;
	export let readonly: boolean = false;
	export let error: boolean = false;
</script>

<div>
	<label for={'epfn-input-' + name}>{label}</label>
	<input
		id={'epfn-input-' + name}
		type="email"
		bind:value
		{name}
		{readonly}
		{required}
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

	input {
		padding: 0.5rem 0.75rem;
		background-color: var(--background-color, gray);
		border-width: 1px;
		border-style: solid;
		border-color: var(--border-color, gray);
		outline-width: 0;
		outline-style: solid;
		outline-color: var(--border-color, gray);
	}

	input:focus-visible {
		outline-width: 1px;
	}

	input:disabled,
	input:read-only {
		cursor: not-allowed;
	}
</style>
