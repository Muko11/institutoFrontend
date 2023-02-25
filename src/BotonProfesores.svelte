<script>
    import { onMount } from "svelte";

    export let tipo = "insertar";
    export let documento = {};
    let clases = "";

    import { getContext } from "svelte";
    import { data } from "./store";
    let URL = getContext("URL");

    let handler = () => {};

    function insertar() {
        let opciones = {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(documento),
        };
        fetch(URL.profesores, opciones)
            .then((res) => res.json())
            // .then((datos) => console.log(datos))
            .then((doc) => ($data = [...$data, doc]))
            .catch((error) => console.log(error));
    }

    function modificar() {
        let opciones = {
            method: "PUT",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(documento),
        };
        fetch(URL.profesores + documento._id, opciones)
            .then((res) => res.json())
            .then((datos) => console.log(datos))
            .catch((error) => console.log(error));
    }

    function eliminar() {
        let opciones = {
            method: "DELETE",
        };
        fetch(URL.profesores + documento._id, opciones)
            .then((res) => res.json())
            // .then((datos) => console.log(datos))
            .then(($data = $data.filter((doc) => doc._id != documento._id)))
            .catch((error) => console.log(error));
    }

    function setup() {
        switch (tipo) {
            case "insertar":
                handler = insertar;
                clases = "btn btn-insertar";
                break;
            case "modificar":
                handler = modificar;
                clases = "btn btn-modificar";
                break;
            case "eliminar":
                handler = eliminar;
                clases = "btn btn-eliminar";
                break;
            default:
        }
    }

    onMount(setup);
</script>

<input type="button" class={clases} value={tipo.toUpperCase()} on:click={handler} />
