<script>
    import {setContext} from "svelte";

    import { Router } from "svelte-routing";
    import Contenido from "./Contenido.svelte";
    import Nav from "./Nav.svelte";

    const URL = {
        libros: "https://libreriabackend.herokuapp.com/api/libros/",
        autores: "https://libreriabackend.herokuapp.com/api/autores/"
    }

    setContext("URL", URL);
	
</script>

<Router>
    <Nav/>
    <Contenido/>
</Router>

<style>

</style>