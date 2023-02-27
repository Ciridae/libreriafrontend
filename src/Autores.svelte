<script>
    import { getContext } from "svelte";
    import { data } from "./store";
    import { onMount } from "svelte";
    import Autor from "./Autor.svelte";
    import Boton from "./Boton.svelte";
    import Buscar from "./Buscar.svelte";

    const URL = getContext("URL");
    let datosFiltrados = [];
    let patron = "";
    let autorInsertar = {};

    let getAutores = async () => {
        const response = await fetch(URL.autores);
        $data = await response.json();
    };

    onMount(getAutores);

    $: datosFiltrados = $data.filter((autor) =>
        RegExp(patron, "i").test(autor.nombre)
    );
</script>

<h1 class="pt-5">Autores</h1>

<div class="row">
    <div class="col-12">
        <div class="contenedor border rounded p-2">
            <Buscar bind:busqueda={patron} />
        </div>
    </div>
    <div class="col-12">
        <div class="contenedor border rounded p-2 mt-3">
            <Autor bind:autor={autorInsertar}>
                <Boton coleccion="autores" documento={autorInsertar} />
            </Autor>
        </div>
    </div>
</div>

<div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 py-3">
    {#each datosFiltrados as autor}
        <div class="col">
            <div class="p-2 border rounded contenedor mb-4">
                <Autor bind:autor>
                    <Boton tipo="modificar" coleccion="autores" documento={autor} />
                    <Boton tipo="eliminar" coleccion="autores" documento={autor} />
                </Autor>
            </div>
        </div>
    {/each}
</div>