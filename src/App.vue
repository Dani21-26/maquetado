<template>
  <div>
    <header>
      <nav id="menu" class="sidebar">
        <h2><a href="./App.vue" style="color: white;">StoreOnce</a></h2>
        <ul>
          <li><a href="#"></a></li>
          <li><a href="#" @click="cargarMonitor">Monitor</a></li>
          <li><a href="#" @click="cargarTabla">Registros</a></li>
          <li><a href="#">Datos</a></li>
          <li><a href="#">Ayuda</a></li>
        </ul>
      </nav>
    </header>
    <main>
    <aside class="cabecera">
      <div class="icono">
        <img src="./assets/icono.jpg" width="50" height="50" @click="abrirMenu" alt="Menú">
      </div>
      <div class="text">
        <h1>Tablero del sistema</h1>
        <p>Unicordoba-vsa</p>
      </div>
    </aside>
<br> <br> <br> <br> <br>
    <div id="contenido-dinamico" class="componente">
      <component :is="componenteActual || 'Contenido'"></component>
    </div>
  </main>
    <footer>
      <!-- Tu código HTML del pie de página -->
    </footer>
  
  </div>
</template>

<script>
// Importa los componentes que deseas cargar dinámicamente
import Contenido from './components/contenido.vue';
import Monitor from './components/Monitor.vue';
import Tabla from './components/Tabla.vue';

export default {
  name: 'App',
  components: {
  Contenido
},

  data() {
    return {
      componenteActual: null,
    };
  },
  methods: {
    abrirMenu() {
      let menu = document.getElementById('menu');
      menu.style.display = menu.style.display === 'none' ? 'block' : 'none';
    },
    cargarMonitor() {
      this.componenteActual = Monitor;
    },
    cargarTabla() {
      this.componenteActual = Tabla;
    },
  },
  mounted() {
    this.cargarContenido();
  },
  cargarContenido() {
    // Carga el contenido inicial si es necesario
    this.componenteActual = null;
  },
};
</script>


<style>
*{
  padding: 0;
  margin: 0;
  list-style: none;
  text-decoration: none;
}
body {
  font-family: 'Roboto', sans-serif;
}
.icono img{
  cursor: pointer;
}
.sidebar {
  position: fixed;
  width: 210px;
  height: 100%;
  background: #40535e;
  transition: all .5s ease;
  font-size: 22px;
  color: white;
  user-select: none;
  text-align: center;
  line-height: 70px;
}
.menu.open {
  transform: translateX(0);
}
.menu h2{
  color: #0e0d0d;
  text-align: center;
  margin-bottom: 20px;
  font-family: Times New Roman;
}
.sidebar ul a{
  display: block;
  height: 100%;
  width: 100%;
  line-height: 60px;
  font-size: 18px;
  color: white;
  padding-left: 40px;
  box-sizing: border-box;
  border-bottom: 1px solid black;
  border-top: 1px solid rgba(255,255,255,.1);
  transition: .4s;
  border-radius:10px
}

ul li:hover a{
  padding-left: 50px;
  background: #908f96;
  
}
.sidebar ul a {
  margin-right: 16px;
  color: #f3f3f3;
}

.cabecera{
  width: 50%;
  position: absolute;
  left: 260px; 
  
}

.text{
  margin: 10px;
  padding: 4px;
  position: absolute;
  left: 40px;
  top: -6px;
}

.componente {
  margin-left: 220px; /* Ajusta el valor según el ancho del menú vertical */
}

</style>
