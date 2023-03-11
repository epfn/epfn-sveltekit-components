<script lang="ts">
	export let name: string;
	export let value: boolean = false;
	export let hidden: boolean = false;
</script>

<div style={hidden ? 'display: none;' : undefined}>
	<input type="checkbox" {name} id={'epfn-input' + name} value={name} bind:checked={value} />
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
