<script>
    import {Link} from "svelte-routing";
</script>

<nav class="navbar navbar-expand-md navbar-dark bg-dark">
    <div class="container-fluid">
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <Link class="nav-link" to="/">Inicio</Link>
          </li>
          <li class="nav-item">
            <Link class="nav-link" to="/libros">Libros</Link>
          </li>
          <li class="nav-item">
            <Link class="nav-link" to="/autores">Autores</Link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

<style>
    nav {
        background-color: antiquewhite;
        padding: 20px;
    }
    
    ul {
        display: flex;
        justify-content: space-evenly;
        list-style-type: none;
    }
</style>