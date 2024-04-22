<!-- eslint-disable vue/multi-word-component-names -->
<template>
<article class="estado">
    <table>
      <thead>
        <h1>Estado</h1>
      </thead>
      <tbody>
        <tr>
          <td>IP servidor: </td>
          <td>
            <p id="circulo"></p>
          </td>
          <td><a href="#">190.200.12.15</a></td>
        </tr>
        <tr>
          <td>Servicio: </td>
          <td>
            <p id="circulo"></p>
          </td>
          <td><a href="#">Web</a></td>
        </tr>
        <tr>
          <td>Tipo: </td>
          <td>
            <p id="circulo"></p>
          </td>
          <td><a href="#">Apache 2.4</a></td>
        </tr>
        <tr>
          <td>Responsables: </td>
          <td>
            <p id="circulo"></p>
          </td>
          <td><a href="#">Darwin Montiel, Daniela Madera</a></td>

        </tr>
      </tbody>
    </table>
  </article>
  <section class="info">
    <section class="info-1">
      <table>
        <thead>
          <h1><Strong>Informacion del sistema</Strong></h1>
        </thead>
        <tbody>
          <tr>
            <td>Nombre</td>
            <td>unicordoba-vsa</td>
          </tr>
          <tr>
            <td>Modelo de plataforma</td>
            <td>HPE StoreOnce VSA</td>
          </tr>
          <tr>
            <td>Hora del sistema</td>
            <td>20/04/2023/ 2:01 PM</td>
          </tr>
          <tr>
            <td>Zona horaria del sistema</td>
            <td>America/Bogota</td>
          </tr>
          <tr>
            <td>Version de software</td>
            <td>4.3.5-2302.20</td>
          </tr>
          <tr>
            <td>Numero de serie</td>
            <td>EYMHUFVEU3DFGHK</td>
          </tr>
          <tr>
            <td>Numero de serie del sistema</td>
            <td></td>
          </tr>
          <tr>
            <td>Numero de serie de la garantia</td>
            <td>PRSW2245299778 <a href="">Mas</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <section class="info-2">
      <div class="logo">
        <img src="../assets/logo.png" alt="editar">
      </div>
      <table>
        <tbody>
          <tr>
            <td>Ubicacion</td>
            <td>AV 1 cr 18 Lorica-cordoba</td>
          </tr>
          <tr>
            <td>Nombre de contacto</td>
            <td>Darwin Montiel</td>
          </tr>
          <tr>
            <td>Numero de contacto</td>
            <td>3479009766</td>
          </tr>
          <tr>
            <td>correo electronico</td>
            <td>DarwinMontiel@Gmail.com</td>
          </tr>
        </tbody>
      </table>

    </section>
  </section>
</template>

<script>
</script>

<style>
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
.estado{
  width: calc(100% - 80%);
  position: absolute;
  left: 260px;
  top: 80px;
}
.estado{
  margin: 1px;
  padding: 15px;
  background-color: rgb(230, 230, 230);
  height: 330px;
  font-size: 13px;
}

#circulo{
  
  background: rgb(17, 167, 3);
  border-radius: 50%;
  width: 10px;
 height: 10px;
  
}
.info{
  width: 56%;
  position: absolute;
  left: 580px;
  top: 80px;
  font-size: 13px;
  
}

.info{
  background-color:  rgb(230, 230, 230);
  padding: 4px;
  height: 350px;
  
  
}

.info-1, td{
  padding: 7px;
  
}

.info-2{
  position: absolute;
  left: 445px;
  top: 10px;
}

.logo img{
  padding: 5px; 
  margin: 10px; 
  float: right; 
  width: 20px;
  color:#908f96;

}
.despliegue {
  cursor: pointer;

}
.mostrando {
  display: block;
}
.oculto{
  display: none;
}

</style>