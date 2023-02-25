<script>
    export let profesor = { nombre: "", asignatura: "" };
</script>

<div class="row datos mx-3 my-3">
    <input
        class="form-control"
        id="nombre"
        type="text"
        placeholder="Nombre"
        bind:value={profesor.nombre}
    /><br />
    <input
        class="form-control"
        id="asignatura"
        type="text"
        placeholder="Asignatura"
        bind:value={profesor.asignatura}
    />

    <slot />
</div>
