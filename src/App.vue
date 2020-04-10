<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input class="search-bar" type="text"  placeholder="Search a place...">
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      api_key: '94488cc198eb4f1c0e56be86d25e9dd3'
    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  #app {
    background-size: cover;
    background-position: bottom;
    transition: 0.5s;
  }

  main {
    background-image: url('./assets/hot.jpg');
    height: 100vh;
    background-size: cover;
    background-position: bottom;
  }

  .search-box {
    margin-left: 290px;
    margin-top: 50px;
    float: left;
  }

  .search-box .search-bar {
    display: inline-block;
    width: 950px;
    height: 80px;
    font-size: 30px;
    font-weight: bold;
    border: 2px solid white;
    background: transparent;
    color: white;
    text-indent: 20px;
    border-top: none;
    border-right: none;
    border-left: none;
    text-align: center;
  }

  .search-bar:focus {
    outline: none;
  }

  ::placeholder {
    color: white;
  }
</style>
