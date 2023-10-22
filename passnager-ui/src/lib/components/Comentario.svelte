<script lang="ts">
	export let label_text: string;
	export let ayuda: string;
</script>

<div>
	<label for="comentario">{label_text}</label>
	<textarea name="comentario" id="comentario" cols="30" rows="10" placeholder={ayuda} />
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
	textarea {
		background-color: #12161b;
		border: 1px solid #ffe86f;
		font-weight: 600;
		border-radius: 5px;
		font-size: 0.85em;
		padding: 5px;
		padding-left: 9px;
		color: #acacac;
	}
</style>
