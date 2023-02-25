<script>
    export let alumno = { nombre: "", curso: "" };
</script>

<div class="row datos mx-3 my-3">
    <input
        class="form-control"
        id="nombre"
        type="text"
        placeholder="Nombre"
        bind:value={alumno.nombre}
    /><br />
    <input
        class="form-control"
        id="curso"
        type="text"
        placeholder="Curso"
        bind:value={alumno.curso}
    />
    <slot />
</div>
