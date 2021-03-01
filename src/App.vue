<template>
  <div id="nav">

<!---aqui encontramos el menu que se mantendra en todas las paginas.-->


    <router-link to="/">Inicio</router-link> 

    <router-link to="/clasificacion">Clasificación</router-link>

    <router-link to="/jornadas">Jornadas</router-link> 

    <router-link to="/partido">Nuevo Partido</router-link> <br>

    <router-link to="/equipos">Equipos</router-link> 

    <router-link to="/jugadores">Jugadores</router-link> 

    <router-link to="/nuevoJugador">Nuevo Jugador</router-link>

    <router-link to="/eliminacion">Eliminar Jugador</router-link>
       
    
  </div>
  <router-view/>
</template>

<style>

#nav {
  
  float: left;
  background-color: bisque;
}
#nav a {
  color: #2c3e50;
  display: block;
  font-size: 30px;

}
#nav a.router-link-exact-active {
  color: red
}
</style>