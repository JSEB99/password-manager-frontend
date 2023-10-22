<script lang="ts">
	export let label_text: string;
</script>

<div>
	<div class="checkbox-container">
		<input type="checkbox" id="roundCheckbox" class="round-checkbox" />
		<label for="roundCheckbox" class="round-label" />
	</div>
	<label class="title" for="roundCheckbox">{label_text}</label>
</div>

<style>
	.checkbox-container {
		display: inline-block;
		vertical-align: middle;
	}
	div {
		font-size: 16px;
	}
	.title {
		font-size: 0.8em;
		vertical-align: middle;
		margin-bottom: 10px;
		color: #ffe86f;
		font-weight: 700;
		margin-right: 5px;
	}
	/* Estilo para ocultar el checkbox predeterminado */
	.round-checkbox {
		position: fixed;
		opacity: 0;
		width: 0;
		height: 0;
	}

	/* Estilo para el contenedor circular */
	.round-label {
		display: inline-block;
		margin-top: 2px;
		width: 15px; /* Ancho del círculo */
		height: 15px; /* Altura del círculo */
		background-color: #12161b; /* Color de fondo del círculo */
		border-radius: 50%; /* Hace que el círculo sea redondo */
		border: 2px solid #ffe86f;
		cursor: pointer;
		position: relative;
	}

	/* Estilo para el círculo interior (marcado) */
	.round-checkbox:checked + .round-label::before {
		content: '';
		width: 70%; /* Tamaño del círculo interior */
		height: 70%; /* Tamaño del círculo interior */
		background-color: #ffe86f; /* Color de fondo del círculo interior cuando está marcado */
		border-radius: 50%; /* Hace que el círculo interior sea redondo */
		display: block;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-52%, -53%);
	}
</style>
