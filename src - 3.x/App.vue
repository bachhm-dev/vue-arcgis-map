<template>
  <div ref="map" class="map">
  </div>
</template>
<script>
  /* eslint-disable */
  import {
    loadModules
  } from 'esri-loader';
  export default {
    mounted() {
      this.loadMap();
    },
    methods: {
      loadMap() {
        loadModules(['esri/map'])
          .then(([Map]) => {
            // create map with the given options
            const map = new Map(this.$refs.map, {
                center: [-56.049, 38.485],
                zoom: 3,
                basemap: 'gray',
              })
              .catch(err => {
                // handle any script or module loading errors
                console.error(err);
              });
          });
      }
    }
  }
</script>
<style>
  /* esri styles */
  @import url('https://js.arcgis.com/3.23/esri/css/esri.css');

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }
</style>