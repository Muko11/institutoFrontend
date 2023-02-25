<script>
    import { getContext } from "svelte";
    import { data } from "./store.js";
    import { onMount } from "svelte";
    import Buscar from "./Buscar.svelte";
    import BotonAlumnos from "./BotonAlumnos.svelte";
    import Alumno from "./Alumno.svelte";

    let alumnoInsertar = {};

    let datosFiltrados = [];
    let patron = "";

    const URL = getContext("URL");

    let getAlumnos = async () => {
        const response = await fetch(URL.alumnos);
        $data = await response.json();
    };

    onMount(getAlumnos);

    $: datosFiltrados = $data.filter((alumno) =>
        RegExp(patron, "i").test(alumno.nombre)
    );
</script>

<div class="container-fluid p-4 p-md-3">
    <h1 class="p-3">Alumnos</h1>

    <p class="px-3">
        <strong>Buscar por nombre</strong>
        <Buscar bind:busqueda={patron} />
    </p>
    <div class="contenedor-insertar">
        <Alumno bind:alumno={alumnoInsertar}>
            <BotonAlumnos documento={alumnoInsertar} />
        </Alumno>
    </div>

    <br />
    <h2 class="p-3">Listado</h2>
    <div class="row row-cols row-cols-md-2 row-cols-lg-3">
        {#each datosFiltrados as alumno}
            <div>
                <Alumno bind:alumno>
                    <div class="row row-cols row-cols-sm-2 mx-0">
                        <BotonAlumnos tipo="modificar" documento={alumno} />
                        <BotonAlumnos tipo="eliminar" documento={alumno} />
                    </div>
                </Alumno>
            </div>
        {/each}
    </div>
</div>
