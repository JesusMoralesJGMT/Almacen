<template>
  <div>
    <div>
      <nav class="navbar navbar-expand-lg navbar-light bg-light" style="background-color: #A8E878;">
        <a class="navbar-brand" href="#">
          <img src="@/assets/316313.png" width="50" height="50" class="d-inline-block align-top" alt="">
        </a>
        <body>
          VENTA DE ELECTRONICA Y EQUIPO DE COMPUTO <br>
          Ciudad Serdán Puebla, México.
        </body>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          
              <!-- <input class="confondo_" type="text" name="nombre" id="IDCONSULTA"  size="30"/>-->
              <v-col
            cols="12"
            sm="10"
             md="8"
            >
            <v-text-field id="IDCONSULTA"
            dense
            label="Consulta"
            ></v-text-field>
             </v-col>
              <div class="input-group-append" id="_consultar">
                <!--<input id="click_Consul" type="submit" value="Consultar" onclick="consultar();"/>-->
                <button class="boton_" v-on:click="Consultar_re">Consultar</button>
                <!-- <button v-on:click="Eliminar_re">Eliminar</button>-->
              </div>  
        </div>
        <div>
          <a class="nav-link" href="#" v-on:click="Muesra_Historial_Clientes">Historial Clientes</a>
        </div>
      </nav>
    </div>
    <div class="content">
      <table v-if="muestra_cie === false">
        <colgroup>
          <col style="background-color: #78B0E8">
          <col span="6" style="background-color:#78E8D7;">
      </colgroup>    <thead>
          <tr style="background-color: black; color:white">
              <th>Id</th>
              <th>Nombre</th>
              <th>Imagen</th>
              <th>Categoria</th>
              <th>Descripción</th>
              <th>Precio</th>
          </tr>
       </thead>
        <tbody v-if="muestra === true"><!--Jesús ->|O.o|-> Estructura de la tabla para mostrar todos los registros-->
            <tr v-for="result in result" v-bind:key="result._id">
              <td> {{result._id}}</td>
              <td> {{result.name}}</td>
              <td> {{result.picture}}</td>
              <td> {{result.category}}</td>
              <td> {{result.description}}</td>
              <td> {{result.price}}</td>
            </tr>
        </tbody>
        <tbody v-if="muestra_ === true"><!--Jesús ->|O.o|-> Estructura de la tabla solo para mostrar el registro consultado-->
          <tr>
            <td> {{result._id}}</td>
            <td> {{result.name}}</td>
            <td> {{result.picture}}</td>
            <td> {{result.category}}</td>
            <td> {{result.description}}</td>
            <td> {{result.price}}</td>
          </tr>
      </tbody>
      </table>
      <table v-if="muestra_cie === true">
        <colgroup>
          <col style="background-color: #f6fa08">
          <col span="8" style="background-color:#f6fa08;">
      </colgroup>    <thead>
          <tr style="background-color: black; color:white">
              <th>Clave del cliente</th>
              <th>Nombre</th>
              <th>Fecha de compra</th>
              <th>Pago</th>
              <th>Clave Producto</th>
              <th>Nombre</th>
              <th>Categoria</th>
              <th>Descripción</th>
          </tr>
       </thead>
       <tbody>
        <tr v-for="His_Cle in His_Cle" v-bind:key="His_Cle._id">
          <td> {{His_Cle._id}}</td>
          <td> {{His_Cle.Nombre}}</td>
          <td> {{His_Cle.Fecha_Compra}}</td>
          <td> {{His_Cle.Pago_Con}}</td>
          <td> {{His_Cle.Producto_compra._id}}</td>
          <td> {{His_Cle.Producto_compra.name}}</td>
          <td> {{His_Cle.Producto_compra.category}}</td>
          <td> {{His_Cle.Producto_compra.description}}</td>
        </tr>
    </tbody>
    </table>
    </div>
    <!--Incio Dirección de cientes-->
    <div v-if="muestra_cie === true">


      <v-card
    class="mx-auto overflow-hidden"
    height="750"
    width="100%"
  >
    <v-system-bar color="deep-purple darken-3"></v-system-bar>

    <v-app-bar
      color="deep-purple accent-4"
      dark
      prominent
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-spacer>
        <div v-if="Entrega === true">
          El producto se encuentra en Camino<br>
        <h5>fecha estimada de entrega: 16/04/2022<br></h5>
        <h5>Hora estimada de entrega: 13:30 hrs<br></h5>
        </div>
      </v-spacer> 
      <div v-if="Entrega === true">
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt="">  
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt=""> 
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt=""> 
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt=""> 
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt="">  
        <img src="@/assets/EnViaje.gif" width="126" height="126" class="d-inline-block align-top" alt="">    
      </div>     
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      bottom
      temporary
      
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item v-on:click="Muestra_Direc">
            <v-list-item-title>Pagina Principal</v-list-item-title>
          </v-list-item>

          <v-list-item v-on:click="Muestra_Direc_">
            <v-list-item-title>Dirección de entrega</v-list-item-title>
          </v-list-item>

          <v-list-item v-on:click="Estado_Entre">
            <v-list-item-title>Estado de la entrega</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-title v-on:click="Observaciones_">Ficha Ciente</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-card-text>
    <section class="mapa">
       <div  v-if="muestra_observaciones === true">
  <v-app>
    <v-card
      class="mx-auto elevation-100"
      color="dark"
      dark
      style="max-width: 400px;"
    >
      <v-row justify="space-between">
        <v-col cols="8">
          <v-card-title>
            <div>
              <div class="text-h5">
                Ana Rosa Baéz
              </div>
              <div>Total de Compras: 12</div>
              <div>Fecha de registro: 2019</div>
            </div>
          </v-card-title>
        </v-col>
        <v-img
          class="shrink ma-2"
          contain
          height="125px"
          src="https://i.pinimg.com/474x/fd/75/f6/fd75f6db79d0a65acc055b17a5418f8d.jpg"
          style="flex-basis: 125px"
        ></v-img>
      </v-row>
      <v-divider dark></v-divider>
      <v-card-actions class="pa-4">
        Calificación de empleado
        <v-spacer></v-spacer>
        <span class="grey--text text--lighten-2 text-caption mr-2">
          ({{ rating }})
        </span>
        <v-rating
          v-model="rating"
          background-color="white"
          color="yellow accent-4"
          dense
          half-increments
          hover
          size="18"
        ></v-rating>
      </v-card-actions>
    </v-card>
  </v-app>
</div>
     <div class="center"  v-if="muestra_mapa === true">
          <div class="columna mapa">
            <iframe src="https://maps.google.com/maps?width=100%25&amp;height=600&amp;hl=es&amp;q=San%20Francisco%20Cuautlancingo,%20Puebla+(San%20Francisco%20Cuautlancingo,%20Puebla)&amp;t=h&amp;z=14&amp;ie=UTF8&amp;iwloc=B&amp;output=embed" width="1200" height="300" frameborder="0" style="border:1" allowfullscreen></iframe>
          </div>
     </div>
     <div v-if="Entrega === true">
       <img src="@/assets/correcto.gif" width="50" height="50" class="d-inline-block align-top" alt="" margin="10px">
       <img src="@/assets/giphy.gif" width="250" height="250" class="d-inline-block align-top" alt="" margin="10px">
       <img src="@/assets/correcto.gif" width="50" height="50" class="d-inline-block align-top" alt="" margin="10px">
       <img src="@/assets/ofd.gif" width="250" height="250" class="d-inline-block align-top" alt="">
       <img src="@/assets/Cargando.gif" width="65" height="65" class="d-inline-block align-top" alt="" margin="10px">
       <img src="@/assets/Localizando.gif" width="250" height="250" class="d-inline-block align-top" alt="">
       <img src="@/assets/Cargando.gif" width="65" height="65" class="d-inline-block align-top" alt="" margin="10px">
       <img src="@/assets/Entregado.gif" width="250" height="250" class="d-inline-block align-top" alt="">
     </div>
    </section>
    </v-card-text>
  </v-card>

    </div>
    <!--Fin de dirección de clientes-->
    <!--Incio Botón-->
    <div v-if="ocultar_crud === true">
       <v-card id="create">
    <v-container fluid>   
    </v-container>
    <v-speed-dial
      v-model="fab"
      :top="top"
      :bottom="bottom"
      :right="right"
      :direction="direction"
      :open-on-hover="hover"
      :transition="transition"
    >
      <template v-slot:activator>
        <v-btn 
          v-model="fab"
          color="blue darken-2"
          dark
          fab
        >
          <v-icon v-if="fab">
            mdi-close
          </v-icon>
          <v-icon v-else>
            mdi-account-circle
          </v-icon>
        </v-btn>
      </template>
      <v-btn @click="Actualizar_re" 
        fab
        dark
        small
        color="#15f600"
      >
        <v-icon>mdi-pencil</v-icon>
      </v-btn>
      <v-btn v-on:click="Insertar_Ven"
        fab
        dark
        small
        color="#288BA8"
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
      <v-btn v-on:click="Eliminar_re"
        fab
        dark
        small
        color="#db0100"
      >
        <v-icon>mdi-delete</v-icon>
      </v-btn>
      <v-btn v-on:click="Muestra_Direc"
        fab
        dark
        small
        color="#FFC300"
      >
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
    </v-speed-dial>
  </v-card>
    </div>
    <!--Fin de dirección de clientes-->
    <!--Inicio de Observaciones-->
    
    <!--Inicio de Observaciones-->
    <div v-if="!imagenes_muestra === false">
      <img src="@/assets/PLAN.png">
      <img src="@/assets/AUD.jpg" width="300" height="300" class="d-inline-block align-top" alt="">
      <img src="@/assets/PLAY5.jpg" width="300" height="300" class="d-inline-block align-top" alt="">
    </div>
    <div v-if="muestravenRe === true">
      <h3 style="text-align:center">Registrando productos</h3>
      <div style="text-align:center">
        <div class="columna">
          <p style="padding-left: 47px;">ID: <input class="confondo" type="text" name="id" id="IDCLAVEPROD"/></p>
          <p>NOMBRE: <input class="confondo" type="text" name="NOMBRE" id="NOMBREPROD"/></p>
          <p>IMAGEN: <input class="confondo" type="text" name="IMAGEN" id="IMAGENPROD"/></p>
        </div>
        <div class="columna">
          <p>DESCRIPCIÓN: <input class="confondo" type="text" name="DESCRIPCION" id="DESCRIPCIONPROD"/></p>
          <p style="padding-left: 47px;">PRECIO: <input class="confondo" type="number" name="PRECIO" id="PRECIOPROD"/></p>
          <p style="padding-left: 1px;">CATEGORIA: <select class="confondo" name="CATEGORIA" id="CATEGORIAPRO">
            <option>computer</option>
            <option>phone</option>
            <option>accesories</option>
          </select></p>
        </div>
        <div class="columna">
          <p>
            <button class="Boton" v-on:click="Insertar"><img src="@/assets/registros.png" alt="x" />Registrar</button>
          </p>
          <p>
            <button class="Boton" v-on:click="CancelarIns"><img src="@/assets/cancelar.png" alt="x" />Cancelar</button>
          </p>
          <p>
            <button class="Boton" v-on:click="LimpiarIns"><img src="@/assets/limpiar-deslizar.png" alt = "x">Limpiar</button>
          </p>
        </div>
      </div>
    </div>
    <!--Actualizar-->
    <div v-if="muesravenAct === true">
      <h3 style="text-align:center">Actualizando productos</h3>
      <div style="text-align:center">
        <div class="columna">
          <p style="padding-left: 47px;">ID: <input class="confondo" type="text" name="id" id="IDCLAVEPROD" readonly/></p>
          <p>NOMBRE: <input class="confondo"  type="text" name="NOMBRE" id="NOMBREPROD"/></p>
          <p>IMAGEN: <input class="confondo" type="text" name="IMAGEN" id="IMAGENPROD" readonly/></p>
        </div>
        <div class="columna">
          <p>DESCRIPCIÓN: <input class="confondo" type="text" name="DESCRIPCION" id="DESCRIPCIONPROD"/></p>
          <p style="padding-left: 47px;">PRECIO: <input class="confondo" type="number" name="PRECIO" id="PRECIOPROD"/></p>
          <p style="padding-left: 1px;">CATEGORIA: <select class="confondo" name="CATEGORIA" id="CATEGORIAPRO">
            <option>computer</option>
            <option>phone</option>
            <option>accesories</option>
          </select></p>
        </div>
        <div class="columna">
          <p>
            <button class="Boton" v-on:click="Insertar_Act"><img src="@/assets/registros.png" alt="x" />Actualizar</button>
          </p>
          <p>
            <button class="Boton" v-on:click="CancelarIns"><img src="@/assets/cancelar.png" alt="x" />Cancelar</button>
          </p>
          <p>
            <!--<button v-on:click="LimpiarIns"><img src="@/assets/limpiar-deslizar.png" alt = "x">Limpiar</button>-->
          </p>
        </div>
      </div>
    </div>
    <!--Fin Actualizar-->
  </div>
</template>

<script>
import axios from "axios";
//let consu = document.getElementById("IDCONSULTA").value;
export default {
  data: () => ({
    result: null,
    His_Cle: null,
    muestra: null,
    muestra_: null,
    muestra_cie: null,
    muestravenRe: null,
    muesravenAct: null,
    imagenes_muestra: true,
    muestra_observaciones: false,
    Login: null,
    Login_:null,
    drawer: false,
    group: null,
    muestra_mapa: false,
    Entrega: true,
    direction: 'bottom',
    fab: false,
    fling: false,
    hover: false,
    tabs: null,
    top: true,
    right: false,
    bottom: false,
    left: true,
    transition: 'slide-x-transition',
    ocultar_crud: null,
    rating: 4.3,
    }),
     watch: {
      top (val) {
        this.bottom = !val
      },
      right (val) {
        this.left = !val
      },
      bottom (val) {
        this.top = !val
      },
      left (val) {
        this.right = !val
      },
      group () {
        this.drawer = false
      }
    },
  created() {//SE CARGAN Y MUESTRAN TODOS LOS REGISTROS. 
  const options = {
      method: 'POST',
      url: 'http://localhost:3000/api/users/login',
      headers: {'Content-Type': 'application/json'},
      data: {email: 'roous.baez@gmail.com', password: 'Baez12345'}
    }
    axios.request(options).then((response) => {
    this.Login = response.data.success;
     if(this.Login){
      axios.get("http://localhost:4027/ConsultarDB/Tabla_Prod").then((result) => {
      this.muestra = true;
      this.muestra_ = false;
      this.muestra_cie = false;
      this.ocultar_crud = true;
      this.result = result.data;
      console.log("fols")
    })
    }
    else{
       alert(response.data.msg)
    }
    })
    
  },
  methods: {
    Observaciones_: function(){//FUNCIÓN PARA VER LAS OBSERVACIONES Y LA CREDENCIAL DEL REGISTRO. 
      this.muestra_observaciones = true;
      this.Entrega = false;
      this.muestra_mapa = false;
    },
    Estado_Entre: function(){//FUNCIÓN PARA MOSTRAR EL ESTADO DE LA ENTREGA.
      this.Entrega = true;
      this.muestra_mapa = false;
      this.muestra_observaciones = false;
    },
    Muestra_Direc: function(){//FUNCION PARA MOSTRAR LA VENTANA PRINCIPAL.
      //this.$router.push('about');
      window.location.href = "http://localhost:8080/about"
      this.muestra_mapa = false
      this.Entrega = false;
       this.muestra_observaciones = false;
    },
    Muestra_Direc_: function(){
      this.muestra_mapa = true;
      this.Entrega = false;
      this.muestra_observaciones = false;
    },
    Consultar_re: function() {//FUNCION PARA CONSULTAR REGISTROS
      //this.result = null
      const options = {
      method: 'POST',
      url: 'http://localhost:3000/api/users/login',
      headers: {'Content-Type': 'application/json'},
      data: {email: 'roous.baez@gmail.com', password: 'Baez12345'}
    }
    axios.request(options).then((response) => {
    this.Login = response.data.success;
     if(this.Login){
        let ConsultaPro = document.getElementById("IDCONSULTA").value; 
      if (ConsultaPro.length < 24){
        alert("La clave deve de contener 24 catarteres")
      }else
        axios.get("http://localhost:4027/"+ConsultaPro).then((result) => {
        this.muestra = false;
        this.muestra_ = true;
        this.muestra_cie = false;
        this.result = result.data;
        this.Entrega = false;
      })
    }
    else{
       alert(response.data.msg)
    }
    })
    },
    Eliminar_re: function() {//FUNCIÓN PARA ELIMINAR UN REGISTRO EN ESPECIFICO
      let ConsultaPro = document.getElementById("IDCONSULTA").value;
      if(!this.muestra_){
        alert("Para eliminar un registro primero debe de realizar la consulta del mismo") 
      }else
      axios.delete("http://localhost:4027/delete/"+ConsultaPro).then((result) =>{
          this.result = result.data;
          location.reload();
        })
    },
    Muesra_Historial_Clientes: function(){//FUNCIÓN PARA CONSULTAR REGISTRO DE HISTORIAL DE CLIENTES
      axios.get("http://localhost:4027/clientes/").then((result) =>{
        this.muestra = false;
        this.muestra_ = false;
        this.muestra_cie = true;
        this.imagenes_muestra= false;
        this.Entrega = false;
        this.ocultar_crud=false;
        this.muestravenRe=false;
        this.His_Cle = result.data;
      })
    },
    Insertar_Ven: function(){//FUNCION PARA CONFIGURAR VENTANA EN MODO INSERCIÓN.
      this.muestravenRe = true;
      this.muesravenAct = false;
      this.imagenes_muestra = false;
      this.muestra_mapa = false;
      this.Entrega = false;
    },
    CancelarIns: function(){//FUNCIÓN PARA CONFIGURAR LA VENTANA AL CANCELAR REGISTRO DE ACTUALIZACIÓN O INSERCIÓN.
      this.muestravenRe = false;
      this.muesravenAct = false;
      this.imagenes_muestra = true;
      this.muestra_mapa = false
      location.reload();

    },
    Actualizar_re: function(){//FUNCIÓN PARA CONFIGURAR LA VENTANA EN MODO ACTUALIZACIÓN.  
      if(!this.muestra_){
        alert("Para actualizar un registro primero debe de consultar el mismo") 
      }else{
      this.muesravenAct = true;
      this.muestravenRe = false;
      this.imagenes_muestra = false;
      this.muestra_mapa = false;
      this.Entrega = false;
      document.getElementById("IDCLAVEPROD").value = this.result._id;
      document.getElementById("NOMBREPROD").value = this.result.name;
      document.getElementById("IMAGENPROD").value = this.result.picture;
      document.getElementById("DESCRIPCIONPROD").value = this.result.description;
      document.getElementById("PRECIOPROD").value = this.result.price;
      document.getElementById("CATEGORIAPRO").value = this.result.category;
      }
    },
    LimpiarIns: function(){//FUNCIÓN PARA LIMPIAR LOS CAMPOS. 
      document.getElementById("IDCLAVEPROD").value = " ";
      document.getElementById("NOMBREPROD").value = " ";
      document.getElementById("IMAGENPROD").value = " ";
      document.getElementById("DESCRIPCIONPROD").value = " ";
      document.getElementById("PRECIOPROD").value = " ";
      document.getElementById("CATEGORIAPRO").value = " ";
    },
    Insertar: function(){//FUNCIÓN PARA INSERTAR UN NUEVO REGISTRO
    const options = {
      method: 'POST',
      url: 'http://localhost:3000/api/users/login',
      headers: {'Content-Type': 'application/json'},
      data: {email: 'roous.baez@gmail.com', password: 'Baez12345'}
    }
    axios.request(options).then((response) => {
    this.Login = response.data.success;
     if(this.Login){
      let _ID         = document.getElementById("IDCLAVEPROD").value; 
      let _NOMBRE     = document.getElementById("NOMBREPROD").value;
      let _IMAGEN     = document.getElementById("IMAGENPROD").value;
      let _DESCIPCION = document.getElementById("DESCRIPCIONPROD").value;
      let _PRECIO     = document.getElementById("PRECIOPROD").value;
      let _CATEGORIA  = document.getElementById("CATEGORIAPRO").value;
      if (_ID === '' || _NOMBRE === '' || _IMAGEN === '' || _DESCIPCION === '' || _PRECIO === '' || _CATEGORIA === ''){
        alert("Debe de llenar todos los campos") 
      }else
         axios.post("http://localhost:4027/post/Ins/"+_ID+"/"+_NOMBRE+"/"+_IMAGEN+"/"+_PRECIO+"/"+_CATEGORIA+"/"+_DESCIPCION).then((result) =>{
          this.result = result.data;
          location.reload();
         })
    }
    else{
      alert(response.data.msg)
    }
    })
    },
    Insertar_Act: function(){//FUNCIÓN PARA ACTUALIZAR UN REGISTRO. 
    const options = {
      method: 'POST',
      url: 'http://localhost:3000/api/users/login',
      headers: {'Content-Type': 'application/json'},
      data: {email: 'roous.baez@gmail.com', password: 'Baez12345'}
    }
    axios.request(options).then((response) => {
    this.Login = response.data.success;
     if(this.Login){
       let _ID         = document.getElementById("IDCLAVEPROD").value; 
      let _NOMBRE     = document.getElementById("NOMBREPROD").value;
      let _IMAGEN     = document.getElementById("IMAGENPROD").value;
      let _DESCIPCION = document.getElementById("DESCRIPCIONPROD").value;
      let _PRECIO     = document.getElementById("PRECIOPROD").value;
      let _CATEGORIA  = document.getElementById("CATEGORIAPRO").value;
      if (_ID === '' || _NOMBRE === '' || _IMAGEN === '' || _DESCIPCION === '' || _PRECIO === '' || _CATEGORIA === ''){
        alert("Valida que todos los campos contengan información") 
      }else
      axios.put("http://localhost:4027/camb/"+_ID+"/"+_NOMBRE+"/"+_PRECIO+"/"+_CATEGORIA+"/"+_DESCIPCION).then((result) =>{
            this.result = result.data;
            this.Consultar_re();
          })
    }
    else{
       alert(response.data.msg)
    }
    })
    }
  }
};
</script>

<style>
  table{
  width:100%; 
  border-collapse:collapse;
}
td{
  border:2px solid black;
}
.columna {
  width:33%;
  float:left;
}
@media (max-width: 500px) {
  
  .columna {
    width:auto;
    float:none;
  }
  
}
.confondo {
  border-radius: 5px;
  border: 1px solid rgb(7, 7, 7);
 }

 .confondo_ {
   background-color: white;
   border-radius: 5px;
  border: 1px solid rgb(7, 7, 7);
 }

.Boton {
   border: 1px solid #2e518b; /*anchura, estilo y color borde*/
padding: 10px; /*espacio alrededor texto*/
background-color: #2e518b; /*color botón*/
color: #ffffff; /*color texto*/
text-decoration: none; /*decoración texto*/
text-transform: uppercase; /*capitalización texto*/
font-family: 'Helvetica', sans-serif; /*tipografía texto*/
border-radius: 50px; /*bordes redondos*/
 }

 .boton_{
    text-decoration: none;
    padding: 3px;
    padding-left: 10px;
    padding-right: 10px;
    font-family: helvetica;
    font-weight: 300;
    font-size: 15px;
    font-style: italic;
    color: #111211;
    background-color: #82b085;
    border-radius: 15px;
    border: 3px double #92d595;
 }
 #create .v-speed-dial {
    position: absolute;
  }

  #create .v-btn--floating {
    position: relative;
  }
</style>