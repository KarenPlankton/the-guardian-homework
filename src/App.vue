<template>
  <div id="app">
    <h1></h1>

   
    <ufo></ufo>
  </div>
</template>

<script>
 import ufo from './components/ufo.vue'


export default {
  name: "App",
  components: {
        ufo
  }
};
</script>

<style>
 

/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.form-item {
  display: flex;
  margin: 0 -10px;
  justify-content: center;
}
.form-item label {
  margin: 0 10px;
}

#push-right {
  margin: 0 20px;
} */
</style>
