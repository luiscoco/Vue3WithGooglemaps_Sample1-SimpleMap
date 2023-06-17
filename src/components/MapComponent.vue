<template>
  <div>
    <div id="map" style="width: 100%; height: 400px"></div>
  </div>
</template>

<script lang="ts">
import { onMounted } from "vue";
import { Loader } from "@googlemaps/js-api-loader";

export default {
  name: "MapComponent",
  setup() {
    onMounted(() => {
      const loader = new Loader({
        apiKey: "AIzaSyBomc_2klMg7y_ZnbTf_Oqg1UyEdEpVJA0",
        version: "weekly",
        libraries: ["places"],
      });

      loader
        .load()
        .then(() => {
          createMap();
        })
        .catch((error) => {
          console.error("Failed to load Google Maps API:", error);
        });
    });

    function createMap(): void {
      const map = new window.google.maps.Map(
        document.getElementById("map") as HTMLElement,
        {
          center: { lat: -34.397, lng: 150.644 },
          zoom: 8,
        }
      );
    }
  },
};
</script>
