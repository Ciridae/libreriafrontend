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

<Buscar bind:busqueda={patron} />

<Autor bind:autor={autorInsertar}>
    <Boton coleccion="autores" documento={autorInsertar} />
</Autor>

{#each datosFiltrados as autor}
    <Autor bind:autor>
        <Boton tipo="modificar" coleccion="autores" documento={autor} />
        <Boton tipo="eliminar" coleccion="autores" documento={autor} />
    </Autor>
{/each}
