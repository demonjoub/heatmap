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
      const center = new google.maps.LatLng(13.770717, 100.583186);
      const options = {
        zoom: 12,
        center: center,
        streetViewControl: false,
        mapTypeControl: false,
        mapTypeId: google.maps.MapTypeId.ROADMAP,
        fullscreenControl: false,
        gestureHandling: "greedy",
        zoomControl: false,
        draggable: false
      };
      this.map = new google.maps.Map(this.$el.querySelector("#map"), options);
      this.google = google;
      this.renderHeatMap();
    },
    renderHeatMap() {
      // ห้วยขวาง
      const google = this.google;
      const heatmapData = [
        new google.maps.LatLng(13.7699, 100.5875),
        new google.maps.LatLng(13.7864, 100.6087),
        new google.maps.LatLng(13.7605, 100.5549),
      ];
      const heatmap = new google.maps.visualization.HeatmapLayer({
        data: heatmapData,
      });

      // บางกะปิ
      const heatmapData2 = [new google.maps.LatLng(13.7628, 100.6456)];
      const heatmap2 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData2,
      });

      // ลาดพร้าว
      const heatmapData3 = [
        new google.maps.LatLng(13.8163, 100.561),
        new google.maps.LatLng(13.8163, 100.571),
        new google.maps.LatLng(13.8263, 100.581),
      ];
      const heatmap3 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData3,
      });

      // บางเขน
      const heatmapData4 = [
        new google.maps.LatLng(13.8644, 100.6146),
        new google.maps.LatLng(13.8744, 100.6246),
      ];
      const heatmap4 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData4,
      });

      // จตุจักร
      const heatmapData5 = [
        new google.maps.LatLng(13.8307, 100.5576),
        new google.maps.LatLng(13.8507, 100.5576),
        new google.maps.LatLng(13.8407, 100.5476),
      ];
      const heatmap5 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData5,
      });

      // วัฒนา
      const heatmapData6 = [new google.maps.LatLng(13.7308, 100.5864)];
      const heatmap6 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData6,
      });

      // สาธร
      const heatmapData7 = [new google.maps.LatLng(13.715, 100.5335)];
      const heatmap7 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData7,
      });

      // คันนายาว
      const heatmapData8 = [new google.maps.LatLng(13.8271, 100.6743)];
      const heatmap8 = new google.maps.visualization.HeatmapLayer({
        data: heatmapData8,
      });

      const zone1 = [
        "rgba(0, 255, 255, 0)",
        "rgba(246,164,192, 1)",
        "rgba(246,164,192, 1)",
        "rgba(239,120,160, 1)",
        "rgba(239,120,160, 1)",
        "rgba(236,79,132, 1)",
        "rgba(236,79,132, 1)",
        "rgba(234,36,98, 1)",
        "rgba(234,36,98, 1)",
        "rgba(228,26,74, 1)",
        "rgba(205,31,68, 1)",
        "rgba(205,31,68, 1)",
        "rgba(179,30,60, 1)",
        "rgba(179,30,60, 1)",
      ];

      const zone2 = [
        "rgba(0, 255, 255, 0)",
        "rgba(252,204,168, 1)",
        "rgba(252,204,168, 1)",
        "rgba(249,175,126, 1)",
        "rgba(249,175,126, 1)",
        "rgba(247,148,89, 1)",
        "rgba(247,148,89, 1)",
        "rgba(244,122,47, 1)",
        "rgba(242,98,35, 1)",
        "rgba(242,98,35, 1)",
        "rgba(230,90,37, 1)",
        "rgba(230,90,37, 1)",
        "rgba(204,81,39, 1)",
        "rgba(204,81,39, 1)",
      ];

      const zone3 = [
        "rgba(0, 255, 255, 0)",
        "rgba(250,246,175, 1)",
        "rgba(250,246,175, 1)",
        "rgba(248,242,132, 1)",
        "rgba(248,242,132, 1)",
        "rgba(246,238,91, 1)",
        "rgba(246,238,91, 1)",
        "rgba(245,237,48, 1)",
        "rgba(243,236,24, 1)",
        "rgba(243,236,24, 1)",
        "rgba(230,230,22, 1)",
        "rgba(230,230,22, 1)",
        "rgba(204,205,42, 1)",
        "rgba(204,205,42, 1)",
      ];

      const zone4 = [
        "rgba(0, 255, 255, 0)",
        "rgba(164,212,152, 1)",
        "rgba(164,212,152, 1)",
        "rgba(126,196,107, 1)",
        "rgba(126,196,107, 1)",
        "rgba(90,187,71, 1)",
        "rgba(90,187,71, 1)",
        "rgba(55,181,74, 1)",
        "rgba(32,175,75, 1)",
        "rgba(32,175,75, 1)",
        "rgba(24,158,73, 1)",
        "rgba(24,158,73, 1)",
        "rgba(19,139,67, 1)",
        "rgba(19,139,67, 1)",
      ];

      const zone5 = [
        "rgba(0, 255, 255, 0)",
        "rgba(157,219,234, 1)",
        "rgba(157,219,234, 1)",
        "rgba(113,206,225, 1)",
        "rgba(113,206,225, 1)",
        "rgba(66,190,216, 1)",
        "rgba(66,190,216, 1)",
        "rgba(17,174,207, 1)",
        "rgba(17,153,187, 1)",
        "rgba(17,153,187, 1)",
        "rgba(22,145,178, 1)",
        "rgba(22,145,178, 1)",
        "rgba(12,129,162, 1)",
        "rgba(12,129,162, 1)",
      ];

      if (this.map) {
        heatmap.set("gradient", heatmap.get("gradient") ? null : zone1);
        heatmap.set("radius", heatmap.get("radius") ? null : 100);
        heatmap.setMap(this.map);

        heatmap2.set("gradient", heatmap2.get("gradient") ? null : zone2);
        heatmap2.set("radius", heatmap2.get("radius") ? null : 100);
        heatmap2.setMap(this.map);

        heatmap3.set("gradient", heatmap3.get("gradient") ? null : zone3);
        heatmap3.set("radius", heatmap3.get("radius") ? null : 100);
        heatmap3.setMap(this.map);

        heatmap4.set("gradient", heatmap4.get("gradient") ? null : zone4);
        heatmap4.set("radius", heatmap4.get("radius") ? null : 100);
        heatmap4.setMap(this.map);

        heatmap5.set("gradient", heatmap5.get("gradient") ? null : zone1);
        heatmap5.set("radius", heatmap5.get("radius") ? null : 100);
        heatmap5.setMap(this.map);

        heatmap6.set("gradient", heatmap6.get("gradient") ? null : zone1);
        heatmap6.set("radius", heatmap6.get("radius") ? null : 100);
        heatmap6.setMap(this.map);

        heatmap7.set("gradient", heatmap7.get("gradient") ? null : zone1);
        heatmap7.set("radius", heatmap7.get("radius") ? null : 100);
        heatmap7.setMap(this.map);

        heatmap8.set("gradient", heatmap8.get("gradient") ? null : zone5);
        heatmap8.set("radius", heatmap8.get("radius") ? null : 100);
        heatmap8.setMap(this.map);
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
