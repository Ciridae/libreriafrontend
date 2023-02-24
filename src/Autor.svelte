<script>
    export let autor = { nombre: "", apellidos: "" };
</script>

<div class="my-3">
    <input type="text" placeholder="Nombre" bind:value={autor.nombre} />&nbsp;
    <input type="text" placeholder="Apellidos" bind:value={autor.apellidos} />
</div>
<slot />