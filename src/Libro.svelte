<script>
    export let libro = { titulo: "", precio: 0 };
</script>

<div class="my-3">
    <input type="text" placeholder="Titulo" bind:value={libro.titulo} />&nbsp;
    <input type="number" placeholder="Precio" bind:value={libro.precio} />
</div>
<slot />
