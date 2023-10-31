<script lang="ts">
	import { onMount } from 'svelte';
	import zxcvbn from 'zxcvbn';
	import Fa from 'svelte-fa';
	import { faCog, faEye, faEyeSlash } from '@fortawesome/free-solid-svg-icons';
	import { faGithub } from '@fortawesome/free-brands-svg-icons';

	let password = '';
	let passwordScore = 0;

	function checkPasswordStrength() {
		const result = zxcvbn(password);
		passwordScore = result.score;
	}

	let showPassword = false;

	function togglePasswordVisibility() {
		showPassword = !showPassword;
	}
</script>

{#if showPassword}
	<input type="text" id="password" bind:value={password} on:input={checkPasswordStrength} />
{:else}
	<input type="password" id="password" bind:value={password} on:input={checkPasswordStrength} />
{/if}

<button on:click={togglePasswordVisibility} class="eye">
	{#if showPassword}
		<Fa icon={faEyeSlash}/>
		<!-- Icono de ojo tachado para ocultar -->
	{:else}
		<Fa icon={faEye} /><!-- Icono de ojo para mostrar -->
	{/if}
</button>

<div id="password-strength-meter">
	<div class="progress-bar" style="width: {passwordScore * 25}%" data-strength={passwordScore} />
	Strength: {passwordScore}
</div>
<Fa icon={faCog} size="3x" spin />
<style>
	.eye {
		width: 32px;
		border-radius: 5px;
		padding: 5px;
		background-color: #12161b;
		border: none;
		color:#ffd609;
		cursor: pointer;
	}
	.eye:hover{
		color: #ffe86f;
	}
	#password {
		margin-bottom: 10px;
	}

	#password-strength-meter {
		font-weight: bold;
		color: #333;
		width: 180px;
	}

	.progress-bar {
		height: 10px;
		background-color: red; /* Cambia el color de fondo base */
		transition: width 0.2s; /* Agrega una transición suave */
		border-radius: 5px;
		padding: 5px;
		height: 4px;
	}

	div {
		font-size: 16px;
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

	/* Establecer los colores de la barra de progreso en función de la fuerza de la contraseña */
	.progress-bar[data-strength='2'] {
		background-color: #ffc04d; /* Amarillo para contraseña moderada */
	}

	.progress-bar[data-strength='3'] {
		background-color: #4db8ff; /* Azul para contraseña fuerte */
	}

	.progress-bar[data-strength='4'] {
		background-color: #5bff4d; /* Verde para contraseña muy fuerte */
	}
</style>
