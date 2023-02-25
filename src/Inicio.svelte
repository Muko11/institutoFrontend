<script>
    import {Link} from "svelte-routing";
</script>

<div class="container">
    <div class="encabezado py-3">
        <h1>INSTITUTO FRONTEND</h1>
        <img src="/imagenes/escuela.png" alt="Instituto" />
    </div>

    <div class="row row-cols-lg-3 mb-5">
        <div class="mt-3">
            <div class="tarjeta text-center">
                <div class="card-body">
                    <h4 class="fw-semibold text-uppercase p-3">Inicio</h4>
                    <p class="p-3">
                        Esta es la página de información de inicio
                    </p>
                    <button class="boton"><Link to="/">Ir a Inicio</Link></button>
                </div>
            </div>
        </div>

        <div class="mt-3">
            <div class="tarjeta text-center">
                <div class="card-body">
                    <h4 class="fw-semibold text-uppercase p-3">Alumnos</h4>
                    <p class="p-3">Operaciones CRUD de alumnos en una BD</p>
                        <Link to="/alumnos"><button class="boton">Ir a Alumnos</button></Link>
                </div>
            </div>
        </div>

        <div class="mt-3">
            <div class="tarjeta text-center">
                <div class="card-body">
                    <h4 class="fw-semibold text-uppercase p-3">Profesores</h4>
                    <p class="p-3">Operaciones CRUD de profesores en una BD</p>
                    <Link to="/profesores"><button class="boton">Ir a Profesores</button></Link>
                </div>
            </div>
        </div>
    </div>

    <div class="alert alert-warning">
        <p class="my-2">
            <strong
                >API Instituto en: <a href="https://institutoapi.onrender.com/"
                    >https://institutoapi.onrender.com/</a
                ></strong
            >
        </p>
    </div>

    <div class="alert alert-warning">
        <p class="my-2">
            <strong
                >Código fuente en: <a
                    href="https://github.com/Muko11/institutoFrontend"
                    >https://github.com/Muko11/institutoFrontend</a
                ></strong
            >
        </p>
    </div>
</div>

<style>
    .encabezado {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    img {
        width: 64px;
        height: 64px;
    }

    a {
        color: darkcyan;
        text-decoration: underline;
    }

    .tarjeta {
        background-color: darkcyan;
        color: white;
    }

    .tarjeta:hover {
        color: black;
        background-color: white;
        border: 1px solid darkcyan;
        transition: 0.5s;
    }

    .boton {
        background-color: lightsalmon;
        font-weight: bold;
        color: white;
        padding: 10px 22px;
        border: 0;
        border-radius: 0;
    }

    .boton:hover {
        background-color: darkcyan;
        text-decoration: underline;
        text-decoration-color: white;
    }

    @media (max-width: 450px) {
        a {
            font-size: 12px;
        }
    }
</style>
