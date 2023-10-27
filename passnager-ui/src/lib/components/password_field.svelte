<script lang="ts">
	import { onMount } from 'svelte';
	import zxcvbn from 'zxcvbn';
  
	let password = '';
	let passwordScore = 0;
  
	function checkPasswordStrength() {
	  const result = zxcvbn(password);
	  passwordScore = result.score;
	}
  </script>
  
  <style>
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
  
  <input type="password" id="password" bind:value={password} on:input={checkPasswordStrength} />
  <div id="password-strength-meter">
	<div class="progress-bar" style="width: {passwordScore * 25}%" data-strength={passwordScore} />
	Strength: {passwordScore}
  </div>