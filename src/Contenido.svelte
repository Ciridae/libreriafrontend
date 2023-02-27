<script>
    import {Route} from "svelte-routing";
    import Autores from "./Autores.svelte";
    import Inicio from "./Inicio.svelte";
    import Libros from "./Libros.svelte";
</script>

<main class="container">
    <Route path="/" component="{Inicio}"></Route>
    <Route path="/libros" component="{Libros}"></Route>
    <Route path="/autores" component="{Autores}"></Route>
</main>