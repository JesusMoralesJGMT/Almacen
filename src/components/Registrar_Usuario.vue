<template>
<!--ABAEZ: 22/04/2022: Se creo diseño para REGISTRAR USUARIO-->
<div>
   <v-app>
   <v-parallax
    dark
    src="https://media3.giphy.com/media/ITRemFlr5tS39AzQUL/giphy.gif?cid=ecf05e47c4b0807ff33e9e92fd98ade66509a8b5b026c8c1&rid=giphy.gif&ct=g"
    height="650"
  >
 
     <v-content>
     <v-container fluid fill-height justify="center">
            <v-layout align-center justify-center>
               <v-flex xs12 sm8 md4>
                  <v-card class="elevation-12">
                     <v-toolbar dark color="#C70039 " >
                        <v-toolbar-title>User register</v-toolbar-title>
                     </v-toolbar>
                     <v-card-text>
                        <v-form>
                           <v-text-field
                              prepend-icon=mdi-account-box
                              id="usuario"
                              name="login"
                              label="Login"
                              type="text"
                           ></v-text-field>
                           <v-text-field
                           id="email" 
                              prepend-icon=mdi-gmail
                              name="correo"
                              label="Email"
                              type="text"
                           ></v-text-field>
                           <v-text-field
                              id="password"
                              prepend-icon="mdi-lock"
                              name="password"
                              label="Password"
                              type="password"
                           ></v-text-field>
                        </v-form>
                     </v-card-text>
                     <template>
                      <div>
                     <v-card-actions>
                        <v-spacer></v-spacer>
                        <!--<router-link class="btn btn-primary " :to="{name:'/about'}">Login</router-link>-->
                        <v-btn v-on:click="Registrar_Usu">Registrar</v-btn>
                        <v-btn v-on:click="Cancelar">Login</v-btn>
                     </v-card-actions>
                       </div>
                       <div v-if="MensajeAler === false">
                            <v-alert type="warning">
                              {{result}}
                            </v-alert>
                       </div>
                       <div v-if="MensajeAler === true">
                            <v-alert type="success">
                                  {{result}}
                             </v-alert>

                       </div>
                     </template>
                  </v-card>
               </v-flex>
            </v-layout>
         </v-container>
   </v-content>
  </v-parallax>
  </v-app>
  
</div>
</template>

<script>
import axios from "axios";
export default {
    data: () => ({
    name: "MiComponente",
    result: null,
    MensajeAler: null
    }),
created() {//SE CARGAN Y MUESTRAN TODOS LOS REGISTROS. 
  
  },
  methods: 
    {
       Registrar_Usu: function(){
            let usuario= document.getElementById("usuario").value;// EVALUA LO QUE CONTENGA EL INPUT 
            let email= document.getElementById("email").value;//EVALUA LO QUE CONTENGA EL INPUT 
            let password= document.getElementById("password").value;//EVALUA LO QUE CONTENGA EL INPUT 
         
var data = JSON.stringify({
  "name": usuario,
  "email": email,
  "password": password
});

var config = {//SE AGREGA URL 
  method: 'post',
  url: 'http://localhost:3000/api/users/register',
  headers: { 
    'Content-Type': 'application/json'//EL FORMATO ES DE TIPO JSON 
  },
  data : data
};
axios.request(config).then((result) => {
    this.result=result.data.msg
  //this.MensajeAler=true 
  if(result.data.success){
      this.MensajeAler=true 
  }else{
      this.MensajeAler=false
  }
})
//axios(config)
//.then(function (result) {
  //alert(result.data.msg);
 
   
//})
 
    },
    Cancelar: function(){//FUNCION PARA MOSTRAR LA VENTANA PRINCIPAL.
      
      window.location.href = "http://localhost:8081/about"
      
    }
}



  }
</script>

<style>
.img_{
  margin-top: 143px;
  margin-left: 500px;
}
</style>