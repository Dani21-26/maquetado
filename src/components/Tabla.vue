<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section class="table-container">
      <table class="table table-striped" id="tabla">
        <thead style="width: 100%; height: 20%;">
          <tr>
            <th>#</th>
            <th>Nombre Servidor</th>
            <th>Sistema Operativo</th>
            <th>Versión</th>
            <th>IP</th>
            <th>Ambiente</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody id="tabla-body">
          <tr v-for="(fila, index) in filas" :key="index">
            <td>{{ index + 1 }}</td>
            <td>
              <template v-if="!fila.editando">{{ fila.nombre }}</template>
              <template v-else>
                <input type="text" v-model="fila.nombreEditado">
              </template>
            </td>
            <td>
              <template v-if="!fila.editando">{{ fila.sistemaOperativo }}</template>
              <template v-else>
                <input type="text" v-model="fila.sistemaOperativoEditado">
              </template>
            </td>
            <td>
              <template v-if="!fila.editando">{{ fila.version }}</template>
              <template v-else>
                <input type="text" v-model="fila.versionEditada">
              </template>
            </td>
            <td>
              <template v-if="!fila.editando">{{ fila.ip }}</template>
              <template v-else>
                <input type="text" v-model="fila.ipEditada">
              </template>
            </td>
            <td>
              <template v-if="!fila.editando">{{ fila.ambiente }}</template>
              <template v-else>
                <input type="text" v-model="fila.ambienteEditado">
              </template>
            </td>
            <td>
              <button @click="editarFila(index)" class="button-primary">
                {{ fila.editando ? 'Guardar' : 'Editar' }}
              </button>
              <button @click="eliminarFila(index)" class="button-primary">Eliminar</button>
            </td>
          </tr>
        </tbody>
      </table>
      <button @click="agregarFila" class="button-primary">Agregar Fila</button>
    </section>
  </template>
  
  <script>
  export default {
    data() {
      return {
        filas: []
      };
    },
    methods: {
      editarFila(index) {
        const fila = this.filas[index];
        if (fila.editando) {
          fila.nombre = fila.nombreEditado;
          fila.sistemaOperativo = fila.sistemaOperativoEditado;
          fila.version = fila.versionEditada;
          fila.ip = fila.ipEditada;
          fila.ambiente = fila.ambienteEditado;
        } else {
          fila.nombreEditado = fila.nombre;
          fila.sistemaOperativoEditado = fila.sistemaOperativo;
          fila.versionEditada = fila.version;
          fila.ipEditada = fila.ip;
          fila.ambienteEditado = fila.ambiente;
        }
        fila.editando = !fila.editando;
      },
      eliminarFila(index) {
        this.filas.splice(index, 1);
      },
      agregarFila() {
        this.filas.push({
          nombre: 'Nombre Servidor',
          sistemaOperativo: 'Sistema Operativo',
          version: 'Versión',
          ip: 'IP',
          ambiente: 'Ambiente',
          editando: false
        });
      }
    }
  };
  </script>

<style>

 /* Estilos de la tabla */
 table {
      border-collapse: collapse;
      width: 100%;
      max-width: 500px;
      margin-bottom: 20px;
    }
    
    th, td {
      text-align: left;
      padding: 8px;
      border-bottom: 1px solid #ddd;
    }
    
    th {
      background-color: #f2f2f2;
    }
    
    /* Estilos del área derecha */
    #product-table-container {
      background-color: #f9f9f9;
      padding: 20px;
    }

    /* -------------------tabla----------------------*/



    .table {
      width: 100%;
      border-collapse: collapse;
    }
    
    .table th,
    .table td {
      padding: 8px;
      text-align: left;
      border-bottom: 1px solid #ddd;
    }
    
    .table th {
      font-weight: bold;
    }
    
    .table-striped tbody tr:nth-child(odd) {
      background-color: #f9f9f9;
    }
    

    .button-primary {
      background-color: #00ff80;
      border-color: #007bff;
      color: #fff;
      padding: 0.375rem 0.75rem;
      font-size: 1rem;
      line-height: 1.5;
      border-radius: 0.25rem;
      cursor: pointer;
    }
    
    .button-primary:hover {
      background-color: #0069d9;
      border-color: #0062cc;
      color: #fff;
    }
    
    .button-primary:focus {
      outline: none;
      box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.5);
    }
    
    .button-primary:active {
      background-color: #0062cc;
      border-color: #005cbf;
      color: #fff;
    }

</style>