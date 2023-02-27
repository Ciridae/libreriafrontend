<script>
    import { getContext } from "svelte";
    import { data } from "./store";
    import { onMount } from "svelte";
    import Buscar from "./Buscar.svelte";
    import Libro from "./Libro.svelte";
    import Boton from "./Boton.svelte";

    const URL = getContext("URL");
    let datosFiltrados = [];
    let patron = "";
    let libroInsertar = {};

    let getLibros = async () => {
        const response = await fetch(URL.libros);
        $data = await response.json();
    };

    onMount(getLibros);

    $: datosFiltrados = $data.filter((libro) =>
        RegExp(patron, "i").test(libro.titulo)
    );
</script>

<h1 class="pt-5">Libros</h1>

<div class="row">
    <div class="col-12">
        <div class="contenedor border rounded p-2">
            <Buscar bind:busqueda={patron} />
        </div>
    </div>
    <div class="col-12">
        <div class="contenedor border rounded p-2 mt-3">
            <Libro bind:libro={libroInsertar}>
                <Boton coleccion="libros" documento={libroInsertar} />
            </Libro>
        </div>
    </div>
</div>

<div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 py-3">
    {#each datosFiltrados as libro}
        <div class="col">
            <div class="p-2 border rounded contenedor mb-4">
                <Libro bind:libro>
                    <Boton
                        tipo="modificar"
                        coleccion="libros"
                        documento={libro}
                    />
                    <Boton
                        tipo="eliminar"
                        coleccion="libros"
                        documento={libro}
                    />
                </Libro>
            </div>
        </div>
    {/each}
</div>
