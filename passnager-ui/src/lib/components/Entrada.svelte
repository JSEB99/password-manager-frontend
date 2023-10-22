<script lang="ts">
	export let titulo: string;
	export let tipo: string;
	export let ayuda: string;
	export let patron: string;
	export let disabled: boolean = false;
</script>

<div>
	<label for="entrada">{titulo}</label>
	<input type={tipo} placeholder={ayuda} id="entrada" pattern={patron} {disabled} />
</div>

<style>
	div {
		font-size: 16px;
	}
	label {
		font-size: 0.8em;
		margin-bottom: 10px;
		color: #ffe86f;
		font-weight: 700;
		display: block;
	}
	input {
		background-color: #12161b;
		border: 1px solid #ffe86f;
		font-weight: 600;
		border-radius: 5px;
		font-size: 0.85em;
		padding: 5px;
		padding-left: 9px;
		color: #acacac;
	}
	input:active {
		color: #acacac;
	}
</style>
