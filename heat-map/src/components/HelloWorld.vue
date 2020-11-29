<template>
  <div class="hello">
    <div id="map"></div>
  </div>
</template>

<script>
import gmaps from "@/gmap/gmap";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      google: null,
      map: null,
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    async init() {
      const google = await gmaps();
      this.geocoder = new google.maps.Geocoder();
      const center = new google.maps.LatLng(13.736717, 100.523186);
      const options = {
        zoom: 13,
        center: center,
        streetViewControl: false,
        mapTypeControl: false,
        mapTypeId: google.maps.MapTypeId.ROADMAP,
        fullscreenControl: true,
        gestureHandling: "greedy",
        zoomControl: true,
      };
      this.map = new google.maps.Map(this.$el.querySelector("#map"), options);
      this.google = google;
      this.renderHeatMap();
    },
    renderHeatMap() {
      const google = this.google;
      const heatmapData = [
        new google.maps.LatLng(13.7699, 100.5875),
        new google.maps.LatLng(13.7864, 100.6087),
        new google.maps.LatLng(13.7605, 100.5549),
      ];
      const heatmap = new google.maps.visualization.HeatmapLayer({
        data: heatmapData,
      });

      const heatmapData2 = [new google.maps.LatLng(13.7628, 100.6456)];
      const heatmap2 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData2,
      });
      const gradient = [
        "rgba(0, 255, 255, 0)",
        "rgba(0, 255, 255, 1)",
        "rgba(0, 191, 255, 1)",
        "rgba(0, 127, 255, 1)",
        "rgba(0, 63, 255, 1)",
        "rgba(0, 0, 255, 1)",
        "rgba(0, 0, 223, 1)",
        "rgba(0, 0, 191, 1)",
        "rgba(0, 0, 159, 1)",
        "rgba(0, 0, 127, 1)",
        "rgba(63, 0, 91, 1)",
        "rgba(127, 0, 63, 1)",
        "rgba(191, 0, 31, 1)",
        "rgba(255, 0, 0, 1)",
      ];

      if (this.map) {
        heatmap.set("radius", heatmap.get("radius") ? null : 100);
        heatmap.setMap(this.map);

        heatmap2.set("gradient", heatmap2.get("gradient") ? null : gradient);
        heatmap2.set("radius", heatmap2.get("radius") ? null : 100);
        heatmap2.setMap(this.map);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  width: 100%;
  height: 100%;
}
#map {
  position: relative;
  width: 100%;
  height: 100%;
}
</style>
