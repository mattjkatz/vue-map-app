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

    // create the popup
    const popup = new mapboxgl.Popup({ offset: 25 }).setText(
      "West Allis, also known as 'Stallis, is home to the Krispy Kreme that I got to."
    );
    // create DOM element for the marker

    const el = document.createElement("div");
    el.id = "marker";

    const marker1 = new mapboxgl.Marker().setLngLat([-87.92, 43.03]).addTo(map);

    // Create a default Marker, colored black, rotated 45 degrees.
    const marker2 = new mapboxgl.Marker({ color: "black", rotation: -30 })
      .setLngLat([-88.007, 43.016])
      // .setLngLat(monument)
      .setPopup(popup) // sets a popup on this marker
      .addTo(map);
    console.log(map, marker1, marker2);
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
#marker {
  background-image: url("https://docs.mapbox.com/mapbox-gl-js/assets/washington-monument.jpg");
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.mapboxgl-popup {
  max-width: 200px;
}
</style>
