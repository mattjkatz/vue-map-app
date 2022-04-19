<template>
  <div class="about">
    <h1>This is a map!</h1>
    <div id="map"></div>
  </div>
</template>

<script>
export default {
  /* global mapboxgl */
  data: function () {
    return {};
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
    const map = new mapboxgl.Map({
      container: "map", // container ID
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-87.92, 43.03], // starting position [lng, lat]
      zoom: 12, // starting zoom
    });
    console.log(map);
  },
};
</script>

<style>
body {
  align-content: center;
  margin: 0;
  padding: 0;
}
#map {
  width: 100vw;
  height: 66vh;
}
</style>
