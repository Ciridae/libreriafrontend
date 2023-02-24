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

<Buscar bind:busqueda={patron} />

<Libro bind:libro={libroInsertar}>
    <Boton coleccion="libros" documento={libroInsertar} />
</Libro>

{#each datosFiltrados as libro}
    <Libro bind:libro>
        <Boton tipo="modificar" coleccion="libros" documento={libro} />
        <Boton tipo="eliminar" coleccion="libros" documento={libro} />
    </Libro>
{/each}
