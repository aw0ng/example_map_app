<template>
  <div class="about">
    <h1>Find Your Way Home</h1>
    <div id="map"></div>
  </div>
</template>

<style>
#map {
  width: 100%;
  height: 500px;
}
</style>

<script>
/* global mapboxgl */

export default {
  mounted: function() {
    this.setupMap();
  },
  methods: {
    setupMap: function() {
      mapboxgl.accessToken =
        "pk.eyJ1IjoicGV0ZXJ4amFuZyIsImEiOiJjazljNjFmNW0wMWgyM2ZxdGJibW5zdDQ1In0.piikxmnHn9k0TnFYjNEoBQ";
      var map = new mapboxgl.Map({
        container: "map", // container id
        style: "mapbox://styles/mapbox/outdoors-v11", // style URL
        center: [-74.0438, 41.1132],
        // startingposition [lng, lat]
        zoom: 9, // starting zoom
      });

      var popup1 = new mapboxgl.Popup({ offset: 50 }).setText("Old Home");
      var popup2 = new mapboxgl.Popup({ offset: 50 }).setText("New Home");

      var marker1 = new mapboxgl.Marker()
        .setLngLat([-74.0754, 40.9445])
        .setPopup(popup1)
        .addTo(map);

      var marker2 = new mapboxgl.Marker()
        .setLngLat([-74.3599, 41.2565])
        .setPopup(popup2)
        .addTo(map);

      console.log(map);
      console.log(marker1);
      console.log(marker2);
      // console.log(marker2);
    },
  },
};
</script>
