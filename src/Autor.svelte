<script>
    export let autor = { nombre: "", apellidos: "" };
</script>

<div class="my-3">
    <input class="form-control mb-2" type="text" placeholder="Nombre" bind:value={autor.nombre} />
    <input class="form-control" type="text" placeholder="Apellidos" bind:value={autor.apellidos} />
</div>
<slot />