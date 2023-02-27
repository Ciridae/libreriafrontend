<script>
    export let libro = { titulo: "", precio: 0 };
</script>

<div class="my-3">
    <input class="form-control mb-2" type="text" placeholder="Titulo" bind:value={libro.titulo} />
    <input class="form-control" type="number" placeholder="Precio" bind:value={libro.precio} />
</div>
<slot />
