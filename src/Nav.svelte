<script>
    import {Link} from "svelte-routing";
</script>


<nav>
	<ul class="mb-0">
		<li><Link to="/">Inicio</Link></li>
		<li><Link to="/alumnos">Alumnos</Link></li>
		<li><Link to="/profesores">Profesores</Link></li>
	</ul>
</nav>

<style>
    nav {
        color: white;
        padding: 10px;
        background-color: darkcyan;
    }

    ul {
        display: flex;
        justify-content: space-around;
        list-style-type: none;
        padding: 10px;
    }

</style>