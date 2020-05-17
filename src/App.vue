<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
export default {
    name: 'app',
    components: {
      Header
    }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetic, sans-serif;
  line-height: 1.4;
  width: 100%;
  padding: 0 10px;
}

#app {
  max-width: 80%;
  margin: 0 auto;
}

.submit-btn {
  display: inline-block;
  background: rgb(44, 44, 44);
  color: white;
  border: none;
}

.submit-btn:hover {
  background: rgb(75, 75, 75);
}
</style>
