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
  data: function() {
    return {
      places: [
        { lat: -25.363, lng: 131.044, description: "A place in Australia" },
        { lat: -33.8675, lng: 151.207, description: "The main city!" },
      ],
    };
  },
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
        zoom: 1, // starting zoom
      });

      this.places.forEach(function(place) {
        var popup = new mapboxgl.Popup({ offset: 50 }).setText(place.description);
        var marker = new mapboxgl.Marker()
          .setLngLat([place.lng, place.lat])
          .setPopup(popup)
          .addTo(map);
        console.log(marker);
        console.log(popup);
      });
    },
  },
};
</script>
