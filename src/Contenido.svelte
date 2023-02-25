<script>
    import {Route} from "svelte-routing";
    import Alumnos from "./Alumnos.svelte";
    import Profesores from "./Profesores.svelte";
    import Inicio from "./Inicio.svelte";
</script>


<main>
    <Route path="/" component="{Inicio}"></Route>
    <Route path="/alumnos" component="{Alumnos}"></Route>
    <Route path="/profesores" component="{Profesores}"></Route>
</main>