<script lang="ts">
	import Entrada from '$lib/components/Entrada.svelte';
	import Comentario from '$lib/components/Comentario.svelte';
	import Categoria from '$lib/components/Categoria.svelte';
	import Checker from '$lib/components/Checker.svelte';
</script>

<Entrada
	tipo={'text'}
	titulo={'Email'}
	ayuda={'Email'}
	patron={'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,}$'}
	disabled={false}
/>
<hr />
<Entrada
	tipo={'password'}
	titulo={'Master Password'}
	ayuda={'Password'}
	patron={'[/w._-!"#$%&/(/)"]{8}'}
	disabled={false}
/>
<hr />
<Comentario label_text={'Notes'} ayuda={'Comments about your password'} />
<hr />
<Categoria />
<hr />
<Checker label_text={'Terms and conditions'} />

<style>
</style>
