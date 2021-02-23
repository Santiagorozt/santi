<template>
  <div id="nav">

<!---aqui encontramos el menu que se mantendra en todas las paginas.-->


    <router-link to="/">Inicio</router-link> 

    <router-link to="/eliminacion">Eliminar Jugador</router-link>
    
    <router-link to="/jugadores">Jugadores</router-link> 

    <router-link to="/jornadas">Jornadas</router-link>    
    
    <router-link to="/equipos">Equipos</router-link> 
    
    <router-link to="/nuevoJugador">Nuevo Jugador</router-link>

    <router-link to="/clasificacion">Clasificación</router-link>

    <router-link to="/partido">Nuevo Partido</router-link> <br>
    
  </div>
  <router-view/>
</template>

<style>

#nav {
  padding: 30px;
  float: left;
}
#nav a {
  color: #2c3e50;
  display: block;
}
#nav a.router-link-exact-active {
  color: red
}
</style>