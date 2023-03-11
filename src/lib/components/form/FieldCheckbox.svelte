<script lang="ts">
	export let name: string;
	export let value: boolean = false;
	export let hidden: boolean = false;
	export let required: boolean = false;
</script>

<div style={hidden ? 'display: none;' : undefined}>
	<input
		id={'epfn-input' + name}
		type="checkbox"
		value={name}
		bind:checked={value}
		{name}
		{required}
	/>
	<label for={'epfn-input' + name}>
		<slot />
	</label>
</div>

<style>
	div {
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}

	label {
		font-weight: normal;
	}
</style>
