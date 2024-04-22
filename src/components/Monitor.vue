<!-- eslint-disable vue/multi-word-component-names -->
<template>
      <section class="monitor">
    <div class="sections-container">
      <div class="section section1">
        <p>Server Up: {{ variablesReactivas.serverUp }}</p>
      </div>
      
      <div class="section section2">
        <p>Servers Development: {{ variablesReactivas.serversDevelopment }}</p>
      </div>
      
      <div class="section section3">
        <p>Server Production: {{ variablesReactivas.serverProduction }}</p>
      </div>
      
      <div class="section section4">
        <p>Server Offline: {{ variablesReactivas.serverOffline }}</p>
      </div>
    </div>

    <div class="button-container">
      <button class="btn-red" @click="mostrarVentana">Mostrar Ventana</button>
      <br> 
      <button class="btn-blue" @click="mostrarPanel = !mostrarPanel">Mostrar Panel</button>
    </div>
  </section>

  <div class="panel" :class="{ 'panel-visible': mostrarPanel }">
    <div class="panel-item">
      <label class="panel-label">Server Up:</label>
      <input class="panel-input" type="text" v-model="variablesReactivas.serverUp">
    </div>

    <div class="panel-item">
      <label class="panel-label">Servers Development:</label>
      <input class="panel-input" type="text" v-model="variablesReactivas.serversDevelopment">
    </div>

    <div class="panel-item">
      <label class="panel-label">Server Production:</label>
      <input class="panel-input" type="text" v-model="variablesReactivas.serverProduction">
    </div>

    <div class="panel-item">
      <label class="panel-label">Server Offline:</label>
      <input class="panel-input" type="text" v-model="variablesReactivas.serverOffline">
    </div>
  </div>
  <section>
    
  </section>

  <section>
    <div  class="ventana" v-if="ventanaVisible">
      <div class="encabezado">
        <table>
             <tr>
               <th>Almacenamiento Local</th>
               <th>Almacenamiento en la Nube</th>
             </tr>
             <tr>
               <td>
                 <div class="storage-bar">
                   <div class="used-space local" :style="{ width: almacenamientoLocalPorcentaje }"></div>
                 </div>
               </td>
               <td>
                 <div class="storage-bar">
                   <div class="used-space cloud" :style="{ width: almacenamientoCloudPorcentaje }"></div>
                 </div>
               </td>
             </tr>
             <tr>
              <td>{{ almacenamientoTotalLocal }} GiB</td>
              <td>{{ almacenamientoTotalCloud }} GiB</td>
             </tr>
             <tr>
               <td>Total</td>
               <td>Total</td>
             </tr>
             <tr>
             <td>
               <div class="used-space-info">
                 <div class="color-box green"></div>
                 <span>Espacio utilizado {{ almacenamientoUsadoLocal }} GiB</span>
               </div>
             </td>
             <td>
               <div class="used-space-info">
                 <div class="color-box green"></div>
                 <span>Espacio utilizado {{ almacenamientoUsadoCloud }} GiB</span>
               </div>
             </td>
           </tr>
           <tr>
             <td>
               <div class="available-space-info">
                 <div class="color-box grey"></div>
                 <span>Espacio libre {{ almacenamientoDisponibleLocal }} GiB</span>
               </div>
             </td>
             <td>
               <div class="available-space-info">
                 <div class="color-box grey"></div>
                 <span>Espacio libre {{ almacenamientoDisponibleCloud }} GiB</span>
               </div> 
             </td>
           </tr>
           </table>

       
        <span class="cerrar" @click="cerrarVentana">X</span>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      mostrarPanel: false,
      ventanaVisible: true,
      arrayCantidades: [
      { server: "www", tam: 20 },
      { server: "DNS", tam: 40 },
      { server: "www", tam: 50 },
      { server: "DNS2", tam: 50 },
    ],
    almacenamientoLocal: 0,
    almacenamientoCloud: 0,
    capacidadTotal: 1000,

    variablesReactivas: {
      serverUp: 10,
      serversDevelopment: 20,
      serverProduction: 40,
      serverOffline: 10
    }
    };
  },
  methods:{
    mostrarVentana() {
      this.ventanaVisible = true;
    },
    cerrarVentana() {
      this.ventanaVisible = false;
    }

  },
  computed: {
    almacenamientoTotalLocal() {
    return this.capacidadTotal;
  },
  almacenamientoTotalCloud() {
    return this.capacidadTotal;
  },
    almacenamientoUsadoLocal() {
    return this.arrayCantidades.reduce(
      (total, { server, tam }) => (server === "www" ? total + tam : total),
      0
    );
  },
  almacenamientoUsadoCloud() {
    return this.arrayCantidades.reduce(
      (total, { server, tam }) => (server === "DNS" || server === "DNS2" ? total + tam : total),
      0
    );
  },
  almacenamientoDisponibleLocal() {
    return this.capacidadTotal - this.almacenamientoUsadoLocal;
  },
  almacenamientoDisponibleCloud() {
    return this.capacidadTotal - this.almacenamientoUsadoCloud;
  },
  almacenamientoLocalPorcentaje() {
    return `${(this.almacenamientoUsadoLocal / this.capacidadTotal) * 100}%`;
  },
  almacenamientoCloudPorcentaje() {
    return `${(this.almacenamientoUsadoCloud / this.capacidadTotal) * 100}%`;
  },
  }
};

</script>


<style> 
.monitor {
  white-space: nowrap;
}

.sections-container {
  margin-bottom: 20px;
}

.button-container {
  display: block;
  justify-content: flex-end;
  text-align: right;
}
.button-container button {
  margin-bottom: 10px;
  margin: 20px;
}

.section {
  display: inline-block;
  width: 200px;
  height: 150px;
  margin-right: 10px;
  margin-bottom: 10px;
  padding: 20px;
  color: white;
  text-align: center;
  border-radius: 10px;
  vertical-align: top;
}


.section1 {
  background-color: rgba(211, 10, 10, 0.829);
}

.section2 {
  background-color: green;
}

.section3 {
  background-color: rgb(178, 226, 5);
}

.section4 {
  background-color: rgb(247, 0, 255);
}
 
.ventana {
    position: fixed;
    top: 70%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 700px;
    height: 300px;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 20px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    z-index: 9999;
  }
  
  .encabezado {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 10px;
  }
  
  .encabezado div {
    flex: 1;
    margin-right: 10px;
  }
  
  .encabezado h3 {
    margin: 0;
  }
  
  .cerrar {
    cursor: pointer;
  }
  
  /**------- CSS de la tabla -------- */

  table {
    border-collapse: collapse;
    width: 100%;
  }

  th, td {
    text-align: center;
    padding: 10px;
    border-radius: 10%;
  }

  .storage-bar {
    background-color: #ddd;
    height: 20px;
    margin-bottom: 10px;
    position: relative;
  }

  .used-space.local {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    background-color: green;
  }

  .used-space.cloud {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    background-color: green;
  }

  .color-box {
    width: 10px;
    height: 10px;
    margin-right: 5px;
    display: inline-block;
  }

  .green {
    background-color: green;
  }

  .grey {
    background-color: grey;
  }

  .panel {
  display: none;
  margin-top: 10px;
  padding: 10px;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
}

.panel-visible {
  display: block;
}

/**----CSS del los Botones---- */


.button-container button {
  margin-bottom: 10px;
}

.btn-red {
    background-color: #ff0000;
    color: #ffffff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 16px;
  }

  .btn-blue {
    background-color: #0000ff;
    color: #ffffff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    font-size: 16px;
  }
/**-----Panel ------------ */

.panel {
    display: none;
    background-color: #f1f1f1;
    padding: 20px;
    margin-top: 10px;
    border-radius: 5px;
    width: 50%;
    height: 40%;
  }

  .panel-visible {
    display: block;
  }

  .panel-item {
    display: flex;
    align-items: center;
    margin-bottom: 10px;
  }

  .panel-label {
    flex: 1;
    margin-right: 10px;
    font-weight: bold;
  }

  .panel-input {
    flex: 2;
    padding: 5px;
    border-radius: 3px;
    border: 1px solid #ccc;
  }
</style>