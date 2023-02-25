<script>
    import { getContext } from "svelte";
    import { data } from "./store.js";
    import { onMount } from "svelte";
    import Buscar from "./Buscar.svelte";
    import BotonProfesores from "./BotonProfesores.svelte";
    import Profesor from "./Profesor.svelte";

    let profesorInsertar = {};

    let datosFiltrados = [];
    let patron = "";

    const URL = getContext("URL");

    let getProfesores = async () => {
        const response = await fetch(URL.profesores);
        $data = await response.json();
    };

    onMount(getProfesores);

    $: datosFiltrados = $data.filter((profesor) =>
        RegExp(patron, "i").test(profesor.nombre)
    );
</script>

<div class="container-fluid p-4 p-md-3">
    <h1 class="p-3">Profesores</h1>

    <p class="px-3">
        <strong>Buscar por nombre</strong>
        <Buscar bind:busqueda={patron} />
    </p>
    <div class="contenedor-insertar">
        <Profesor bind:profesor={profesorInsertar}>
            <BotonProfesores documento={profesorInsertar} />
        </Profesor>
    </div>

    <br />
    <h2 class="p-3">Listado</h2>
    <div class="row row-cols row-cols-md-2 row-cols-lg-3">
        {#each datosFiltrados as profesor}
            <div>
                <Profesor bind:profesor>
                    <div class="row row-cols row-cols-sm-2 mx-0">
                        <BotonProfesores
                            tipo="modificar"
                            documento={profesor}
                        />
                        <BotonProfesores tipo="eliminar" documento={profesor} />
                    </div>
                </Profesor>
            </div>
        {/each}
    </div>
</div>
