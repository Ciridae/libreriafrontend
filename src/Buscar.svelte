<script>
    export let busqueda = "";
</script>

<label for="buscar">Buscar:</label>
<input id="buscar" class="form-control" type="search" bind:value={busqueda}>