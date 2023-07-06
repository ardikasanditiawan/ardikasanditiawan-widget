<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li><router-link to="/">Cuaca</router-link></li>
          <li><router-link to="/location">Lokasi</router-link></li>
          <li><router-link to="/stopwatch">Penghitung Detik</router-link></li>
          <li><router-link to="/TicTacToeWidget">Tic Tac Toe</router-link></li>
          <li><router-link to="/photo">Foto</router-link></li>
        </ul>
      </nav>
    </header>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>

#app {
  text-align: center;
  
  
}


header {
  background: #013c44;
  padding: 22px;
  border-radius: 3px;
  
}

nav ul {
  list-style:circle;
  margin: 0;
  padding: 0;
  
  
}

nav li {
  display:inline-block;
  margin-right: 3px;
  background-color: rgb(255, 255, 255);
  padding: 10px;
  border-radius: 3px;

}

nav a {
  color: #000000;
  text-decoration: none;
  padding: 65px;
  
}

nav a:hover {
  text-decoration: underline;
  color: rgb(98, 0, 255);

}
</style>
