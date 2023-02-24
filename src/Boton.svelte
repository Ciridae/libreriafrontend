<script>
    import { onMount } from "svelte";
    import { getContext } from "svelte";
    import { data } from "./store";

    export let tipo = "insertar";
    export let documento = {};
    export let coleccion = "";

    let enlace = "";
    let URL = getContext("URL");

    if (coleccion == "libros") {
        enlace = URL.libros;
    } else if (coleccion == "autores") {
        enlace = URL.autores;
    }

    let handler = () => {};

    function insertar() {
        let opciones = {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(documento),
        };
        fetch(enlace, opciones)
            .then((res) => res.json())
            .then((doc) => ($data = [...$data, doc]))
            .catch((error) => console.log(error));
    }

    function modificar() {
        let opciones = {
            method: "PUT",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(documento),
        };
        fetch(enlace + documento._id, opciones)
            .then((res) => res.json())
            .then((datos) => console.log(datos))
            .catch((error) => console.log(error));
    }

    function eliminar() {
        let opciones = {
            method: "DELETE",
        };
        fetch(enlace + documento._id, opciones)
            .then((res) => res.json())
            .then(($data = $data.filter((doc) => doc._id != documento._id)))
            .catch((error) => console.log(error));
    }

    function setup() {
        switch (tipo) {
            case "insertar":
                handler = insertar;
                break;
            case "modificar":
                handler = modificar;
                break;
            case "eliminar":
                handler = eliminar;
                break;
            default:
                break;
        }
    }

    onMount(setup);
</script>

<input type="button" value={tipo.toUpperCase()} on:click={handler} />
